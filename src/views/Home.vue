<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" class="m-4" /> -->

    <Characters />

    <div class="text-center m-20">
      <router-link to="./about">Wat info over mij? klik hier..</router-link>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

import Characters from "@/components/Characters.vue";
// import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

@Component({
  components: {
    Characters
  }
})
export default class Home extends Vue {}
</script>
