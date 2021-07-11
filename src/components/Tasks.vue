<template>
  <div @click="$emit('toggle-remainder',task.id)"
   :class="[task.remainder ? 'remainder' : '', 'task']">
    <h3>
      {{ task.day }}
      <font-awesome-icon
        @click="$emit('delete-item',task.id)"
        class="faDeleteIcom"
        :icon="faDelete"
      />
    </h3>
    <p>{{ task.text }}</p>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faTimes } from "@fortawesome/free-solid-svg-icons";

export default {
  name: "Tasks",

  props: {
    task: Object,
  },
  data() {
    return {
      faDelete: faTimes,
    };
  },
  components: {
    FontAwesomeIcon,
  },


};
</script>

<style scope>
.task {
  padding: 20px;
  margin: 20px;
  border-radius: 10px;
  background-color: rgba(204, 204, 201, 0.699);
  width: 40%;
  cursor: pointer;
}
.task.remainder {
  border-left: 5px solid greenyellow;
}
.faDeleteIcom {
  color: red;
  margin-left: 20px;
}
</style>
