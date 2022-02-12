<template>
  <div>
    <h1>Contact {{ name }}</h1>
    <h1>{{ description }}</h1>
  </div>
</template>

<script>
export default {
  props: {
    name: { type: String },
    description: { type: String },
  },
};
</script>

<style></style>
