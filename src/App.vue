<template>
  <div class="box">
    <nested-draggable :tasks="list" />
  </div>
</template>

<script>
import nestedDraggable from "./components/nested.vue";
export default {
  components: {
    nestedDraggable
  },
  data() {
    return {
      list: [
        {
          id: 1,
          depth: 0,
          name: "cat 1",
          tasks: [
            {
              id: 2,
              depth: 1,
              name: "cat 2",
              tasks: []
            }
          ]
        },
        {
          id: 3,
          depth: 0,
          name: "cat 3",
          tasks: [
            {
              id: 4,
              depth: 1,
              name: "cat 4",
              tasks: []
            }
          ]
        },
        {
          id: 5,
          depth: 0,
          name: "cat 5",
          tasks: []
        }
      ]
    };
  }
};
</script>
<style scoped>
.box {
  width: 400px;
  background: #555;
}
</style>