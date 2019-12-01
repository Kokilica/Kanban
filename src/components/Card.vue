<template>
  <div id="cards">
    <div
      :id="id"
      class="card"
      :draggable="draggable"
      v-on="getTaskData"
      @dragstart="dragStart"
      @dragover.stop
    >
      <div v-for="(taskData, index) in taskList" :key="index">
        <div v-if="taskData.name === 'TO DO'">
          <span>{{ taskData.items[index].title }}</span>
          <hr />
          <span>{{ taskData.items[index].text }}</span>
        </div>
        <!--<div v-else-if="taskData.name === 'IN PROGRESS'">
          <span>{{ taskData.items[index].title }}</span>
          <hr>
          <span>{{ taskData.items[index].text }}</span>
        </div>-->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    return {
      taskList: []
    };
  },
  props: ["id", "draggable", "cards"],
  methods: {
    dragStart: e => {
      const target = e.target;
      e.dataTransfer.setData("card_id", target.id);
      setTimeout(() => {
        target.style.display = "none";
      }, 0);
    },
    getTaskData() {
      fetch("sample.json")
        .then(response => response.json())
        .then(data => (this.taskList = data));
    }
  },
  mounted() {
    this.getTaskData();
  }
};
</script>

<style lang="scss" scoped>
</style>