<template>
  <div class="container">
    <h1>{{ titulo }}</h1>
    <ul class="card-container">
      <li v-for="digimon in digimons">
        <card class="card">
          <h1 class="card-text">{{ digimon.name }}</h1>
          <img :src="digimon.img" alt="" class="card-image" />
          <span class="card-stats">
            {{ digimon.level }}
          </span>
        </card>
      </li>
    </ul>
  </div>
</template>

<script>
import Card from "./components/shared/Card/index.vue";

components: {
  card: Card;
}

export default {
  data() {
    return {
      titulo: "Digiman Card",
      digimons: this.digimons
    };
  },

  created() {
    this.$http
      .get("https://digimon-api.vercel.app/api/digimon")
      .then(res => res.json())
      .then(data => {
        this.digimons = data;
        console.log(this.digimons);
      });
  }
};
</script>

<style>
.container {
  display: grid;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  gap: 10px;
  align-items: center;
  padding-left: 80px;
  padding-right: 80px;
  justify-content: center;
  align-items: center;
  justify-items: center;
}

.card-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 50px;
  list-style: none;
}

.card {
  display: grid;
  grid-template-columns: 300px;
  grid-template-rows: 250px 100px 80px;
  grid-template-areas: "image" "text" "stats";
  background: #ffffff;
  border-radius: 18px;
  width: 300px;
  align-items: center;
  justify-items: center;
  box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.6);

  transition: 0.2s;
}

.card:hover {
  transform: scale(1.15);
  box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.6);
}

.card .card-text {
  color: rgb(0, 0, 0);
  font-size: 50px;
  font-weight: 300;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  align-self: flex-end;
}

.card .card-image {
  grid-area: image;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
  background-size: cover;
  height: 200px;
}

.card .card-stats {
  grid-area: stats;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 30px;
  color: rgb(133, 133, 133);
}
</style>
