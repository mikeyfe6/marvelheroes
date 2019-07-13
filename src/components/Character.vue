<template>
  <div class="Character">
    <h1>Detailpagina van je favoriete Marvel Hero!</h1>
    <p>{{ this.$route.params.id }}</p>
  </div>
</template>

<script>
export default {
  name: "Character"
};
</script>

<style>
</style>
