<template>
  <draggable
    class="dragArea"
    tag="ul"
    :list="tasks"
    :group="{ name: 'g1', put: (toSortable, fromSortable, draggedElement) => topLevelContainerFilter(toSortable, fromSortable, draggedElement) }"
    item-key="name"
  >
    <template #item="{ element }">
      <li>
        <p>{{ element.name }}</p>
        <nested-draggable :tasks="element.tasks" />
      </li>
    </template>
  </draggable>
</template>
<script>
import draggable from "vuedraggable";
export default {
  name: "nested-draggable",
  components: {
    draggable
  },
  props: {
    tasks: {
      required: true,
      type: Array
    }
  },
  methods: {
    topLevelContainerFilter(toSortable, fromSortable, draggedElement) {
      let isElement = (fromSortable.options.group.name === 'g1');
      let notContainerOrTopLevel = (toSortable.el.classList.contains('top__level') || !draggedElement.classList.contains('g1'))
      
      console.log('toSortable.el', toSortable.el)
      return isElement && notContainerOrTopLevel;
    }
  }
};
</script>
<style scoped>
.dragArea {
  margin: 0;
  padding: 0;
}

li {
  list-style: none;
  background-color: #555;
  padding-left: 20px;
}

li p {
  padding-top: 8px;
  padding-bottom: 8px;
  color: black;
  cursor: grab;
}

</style>