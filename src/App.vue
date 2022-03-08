<template>
  <div>
    <h1>{{ titulo }}</h1>
    <ul>
      <li v-for="digimon in digimons" >
        <p>the digimon {{ digimon.name }}</p>
        <img :src="digimon.img" alt="">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "Pokemon Pic",
      digimons: this.digimons,
    };
  },

  created() {
    this.$http.get("https://digimon-api.vercel.app/api/digimon")
    .then(res => res.json())
    .then(data => {
      this.digimons = data;
          console.log(this.digimons);
    });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
