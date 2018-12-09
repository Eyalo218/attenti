<template>
  <div class="home">
    <business-grid></business-grid>
  </div>
</template>

<script>
// @ is an alias to /src
import BusinessGrid from "../components/BusinessGrid.vue";
export default {
  components: {
    BusinessGrid
  }
};
</script>

<style scoped>
.home {
  width: 80%;
  margin: 0 auto;
}
</style>
