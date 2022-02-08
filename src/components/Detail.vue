<template>
  <v-container>
    <h1>product detail</h1>
    <h1>ID = {{ $route.params.id }}</h1>
    <h2 class="orange--text">{{ productid }}</h2>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      productid: this.$route.params.id,
    };
  },
};
</script>

<style></style>
