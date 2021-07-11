<template>
  <div class="info-btn">
    <button class="btn-primary"
      @click="onClickHandler()"
     :style="{backgroundColor:color,cursor:'pointer'}">{{text}}</button>
  </div>
</template>
 
<script>
export default {
  name: "Info",
 
 props:{
   text:String,
   color:String,
 },

  methods: {
    onClickHandler() {
      
      this.$emit('toggle-button');
      
    }
  },




};
</script>

<style scoped>
.btn-primary {
  background-color: green;
  cursor: pointer;
  padding: 13px;
  border-radius: 10px;
}
</style>

