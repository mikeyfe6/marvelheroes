<template>
  <header class="AppHeader border-t-8 border-teal-700">
    <nav class="container mx-auto flex justify-between items-center p-4 py-8">
      <router-link to="/" class="hover:text-red-300">LOGO|MF</router-link>
      <ul class="uppercase tracking-wide font-bold flex items-center">
        <li class="mr-4">
          <router-link to="/" class="hover:text-red-300">Home</router-link>
        </li>
        <li>
          <router-link to="/about" class="hover:text-red-300">About</router-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: "AppHeader"
};
</script>

<style>
</style>
