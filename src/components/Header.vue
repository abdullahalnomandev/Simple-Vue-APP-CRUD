<template>
  <div class="info">
    <h1>{{ title }}</h1>
    <Button @toggle-button="$emit('toggle-button')" text="Add  Task" color="green" />
  </div>
</template>

<script>
import Button from "./Info.vue";

export default {
  components: { Button },
  name: "Header",
  props: {
    title: String,
  },
};
</script>

<style>
.info {
  display: grid;
  justify-content: center;
  align-items: center;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  color: #0b060c;
  margin: 0px 100px;
  padding: 20px;
}

</style>
