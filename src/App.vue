<template>
  <div id="app">
    <div class="text-red-800 leading-normal flex flex-col min-h-screen">
      <AppHeader />
      <div class="flex-grow">
        <div class="hero container-inner mx-auto py-16">
          <router-view />
        </div>
      </div>
      <AppFooter />
    </div>
  </div>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";
import AppHeader from "./components/AppHeader";
import AppFooter from "./components/AppFooter";

@Component({
  components: {
    AppHeader,
    AppFooter
  }
})
export default class App extends Vue {}
</script>


<style lang="scss">
</style>
