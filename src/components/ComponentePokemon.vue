<template>
  <div class="hello">
    <p>
      Estas buscando al pokemon <strong>{{ pokeName }}</strong>
    </p>
    <div>
      <label>
        <input
          v-model="pokemon.name"
          @keyup.enter="getData"
          type="text"
          class="busqueda"
        />
        <button @click="getData" class="button">Buscar pokemon</button>
      </label>
    </div>
    <div class="image">
      <img :src="pokeFotos" alt="" />
    </div>
    <div>
      <h2><u>Movimientos</u></h2>
      <div class="lista">
        <ul>
          <li
            v-for="(movimiento, index) in pokeMovimientos"
            v-bind:key="index"
            v-text="movimiento.move.name"
          ></li>
        </ul>
      </div>
    </div>
    <div>
      <h2><u>Habilidades</u></h2>
      <div class="lista">
        <ul>
          <li
            v-for="(habilidades, index) in pokeHabilidades"
            v-bind:key="index"
            v-text="habilidades.ability.name"
          ></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ComponentePokemon",
  props: {},
  data() {
    return {
      pokemon: {
        name: "pikachu",
        moves: [],
        abilities: [],
        sprites: {
          front_default: "",
        },
      },
    };
  },
  created() {
    this.getData();
  },
  methods: {
    getData() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon.name}`)
        .then((response) => response.json())
        .then((json) => (this.pokemon = json));
      console.log(this.getData);
    },
  },
  computed: {
    pokeMovimientos() {
      return this.pokemon.moves;
    },
    pokeFotos() {
      return this.pokemon.sprites.front_default;
    },
    pokeHabilidades() {
      return this.pokemon.abilities;
    },
    pokeName() {
      return this.pokemon.name;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.lista {
  list-style-type: none;
  padding: 0;
  background-color: #75751586;
  border: 4px solid #7562c9;
  width: 35%;
  margin: auto;
  height: auto;
  border-radius: 10px;
}
li {
  display: inline-block;
  margin: 0 10px;
}
.busqueda {
  background-color: #e1fa00d5;
  width: 300px;
  height: 20px;
  border: 3px solid rgb(8, 8, 8);
  font-weight: bold;
  font-size: 20px;
}
.button {
  background-color: #3c279b;
  color: rgb(248, 248, 248);
  border: 3px solid rgb(8, 8, 8);
  border-radius: 5px;
  width: 200px;
  height: 30px;
  margin: 10px;
  margin-top: 20px;
  font-weight: bold;
  font-size: 20px;
}
.image {
  background-color: #75751586;
  border: 4px solid #7562c9;
  width: 35%;
  margin: auto;
  height: auto;
  border-radius: 10px;
}
</style>
