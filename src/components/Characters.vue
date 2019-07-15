<template>
  <div class="Characters">
    <div class="card-container">
      <div class="card p-10" v-for="character in characters" v-bind:key="character.id">
        <router-link
          class="text-xl cstmrt"
          :to="{ name: 'character', params: { id: character.id }}"
        >{{ character.name }}</router-link>
        <img class="inline mt-5" :src="url" alt />
      </div>
    </div>
  </div>
</template>

<script>
import { public_key, secret_key } from "@/marvelsecret.ts";
import axios from "axios";
import Character from "./Character";

export default {
  name: "Characters",

  components: {
    Character
  },

  data() {
    return {
      characters: [],
      url: "",
      size: "standard_large.jpg"
    };
  },

  mounted() {
    this.getCharacters();
  },

  methods: {
    getCharacters: function() {
      axios
        .get(
          `http://gateway.marvel.com/v1/public/characters?apikey=${public_key}`
        )
        .then(result => {
          result.data.data.results.forEach(item => {
            console.log(item);

            this.characters.push(item);

            this.url = `${item.thumbnail.path}/${this.size}`;

            console.log(this.url);
          });
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>

<style lang="scss">
.card {
  text-align: center;
  background-color: rgb(202, 202, 202);
  border-radius: 30px;
  min-height: 200px;
}

.card-container {
  display: grid;
  grid-template-columns: auto auto auto;
  grid-gap: 30px;
}

.cstmrt {
  color: goldenrod;
}
</style>
