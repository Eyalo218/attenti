<template>
  <table>
    <tr>
      <th class="type">Type</th>
      <th class="topic">Topic Name
        <!-- <sub>&25BC</sub> -->
      </th>
      <th class="documents">Positive Training Documents</th>
      <th class="actions">Actions</th>
      <hr class="bold">
    </tr>
    <tr v-for="(row,i) in tableData" :key="i" :id="i">
      <td class>{{row.type}}</td>
      <td class>{{row.topic_name}}</td>
      <td class>
        {{row.doc_num}}
        <span v-show="(row.doc_num<200)">
          <img class="icon" src="/icons/alert.png" alt>
          (need a 200 minimum)
          <sup>add documents</sup>
        </span>
        <hr>
      </td>
      <td class>
        <actions-component @delete-data="deleteItem" @edit-topic="editTopic" :typeNum="row.type"></actions-component>
      </td>
    </tr>
  </table>
</template>

<script>
import ActionsComponent from "./ActionsComponent.vue";

export default {
  props: {
    tableData: {
      type: Array
    }
  },
  components: {
    ActionsComponent
  },
  methods: {
    deleteItem(index) {
      this.tableData.splice(index, 1);
    },
    editTopic(data) {
      this.tableData[data["index"]].topic_name = data.newTopic;
    }
  }
};
</script>

<style>
table {
  width: 100%;
}
th {
  text-align: left;
}

.bold {
  border: black solid 1.3pt;
  border-radius: 50px;
}
</style>
