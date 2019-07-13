<template>
  <div class="Characters">
    <h1>Hallo, hier kan je een lijst vinden van de Marvel Heroes</h1>
    <br />
    <ul>
      <li v-for="character in characters" v-bind:key="character.id">
        <router-link :to="{ name: 'character', params: { id: character.id }}">{{ character.name }}</router-link>
      </li>
    </ul>
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
      characters: []
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
          });
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>

<style>
</style>
