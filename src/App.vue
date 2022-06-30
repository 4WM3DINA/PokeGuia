<template>
  <div id="app">
    <h1>Poke-Guia</h1>
    <ComponentePokemon />
  </div>
</template>

<script>
import ComponentePokemon from "./components/ComponentePokemon.vue";

export default {
  name: "App",
  components: {
    ComponentePokemon,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  background-image: url("https://www.gratistodo.com/wp-content/uploads/2016/07/pokemon-wallpapers-22.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  width: 100vw;
  height: auto;
  border: 10px double #7562c9;
  color: rgb(3, 3, 3);
  font-weight: bold;
  font-size: 18px;
}
</style>
