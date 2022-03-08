<template>
  <div class="card">
    <h2 class="card-title">{{ titulo }}</h2>
    <slot class="card-content"></slot>
  </div>
</template>

<script>
export default {
  props: ["titulo"]
};
</script>

<style scoped>
.card {
  display: grid;
  grid-template-columns: 300px;
  grid-template-rows: 210px 210px 80px;
  grid-template-areas: "image" "text" "stats";
  background: red;
  color: red;
  border-radius: 18px;

}

.card .card-title {
  text-align: center;
  border: solid 2px;
  background: lightblue;
  margin: 0 0 15px 0;
  padding: 10px;
  text-transform: uppercase;
}

.card .card-content {
  grid-area: image;
  background: red;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
  background-size: cover;
}
</style>
