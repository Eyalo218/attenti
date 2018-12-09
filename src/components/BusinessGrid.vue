<template>
  <div class="business-grid">
    <header-component></header-component>
    <grid-view :tableData="businessData['data']"></grid-view>
  </div>
</template>

<script>
import dataService from "../services/dataService.js";
import HeaderComponent from "./HeaderComponent.vue";
import GridView from "./GridView.vue";

export default {
  components: { dataService, HeaderComponent, GridView },
  data() {
    return {
      businessData: dataService.getData()
    };
  }
};
</script>

<style>
</style>
