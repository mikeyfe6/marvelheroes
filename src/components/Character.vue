<template>
  <div class="Character">
    <h1 class="mb-10">Detailpagina van je favoriete Marvel Hero!</h1>
    <div class="mrvflex-container">
      <div class="mrvflexone" v-for="char in character" v-bind:key="char.id">
        <h3>{{ char.name }}</h3>
        <br />
        <p>{{ char.description }}</p>
      </div>
      <div class="mrvflextwo">
        <img class="mrv-img" :src="url" alt />
      </div>
      <!-- <p>{{ this.$route.params.id }}</p> -->
    </div>
    <router-link to="/">
      <button
        class="bg-white hover:bg-gray-100 font-semibold py-2 px-4 border border-gray-400 rounded shadow mt-8"
      >Back</button>
    </router-link>
  </div>
</template>

<script>
import { public_key } from "../marvelsecret";
import axios from "axios";
export default {
  name: "Character",

  data() {
    return {
      character: [],
      url: "",
      size: "standard_large.jpg"
    };
  },

  mounted() {
    this.getCharacter();
  },

  methods: {
    getCharacter: function() {
      var characterId = this.$route.params.id;

      axios
        .get(
          `http://gateway.marvel.com/v1/public/characters/${characterId}?apikey=${public_key}`
        )
        .then(result => {
          console.log(result);

          result.data.data.results.forEach(item => {
            this.character.push(item);

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
.mrvflex-container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.mrvflexone {
  flex: 60%;
}

.mrvflextwo {
  flex: 40%;
}

.mrv-img {
  width: 70%;
  margin-left: 1rem;
  border-radius: 30px;
}
</style>
