<template>
  <div class="container">
    <h1>{{ titulo }}</h1>
    <ul>
      <li v-for="digimon in digimons">
        <card>
          {{ digimon.name }}
          <img :src="digimon.img" alt="" />
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
      titulo: "Pokemon Pic",
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
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
