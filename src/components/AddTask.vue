<template>
  <form @submit="onSubmit" action="" class="add-form">
    <div class="form-control">
      <label for="">Task </label><br />
      <input
        type="text"
        v-model="text"
        name="text"
        id=""
        placeholder="Add Task"
        required
      /><br />
    </div>

    <div class="form-control">
      <label for="">Day & Time</label><br />
      <input
        type="text"
        v-model="day"
        name="day"
        id=""
        placeholder="Add Day & Time"
        required
      /><br />
    </div>

    <div class="form-control from-control-check">
      <label>Set Remainder</label>
      <input
        type="checkbox"
        v-model="remainder"
        name="remainder"
        id=""
   
      />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      remainder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.text) {
        alert("Please  add a task");
        return;
      }
      
      const newTask ={
        id:Math.floor(Math.random()*1000),
        text:this.text,
        day: this.day,
        remainder:this.remainder
      }

      this.$emit('new-task',newTask);

      console.log('newTask',newTask);

      this.text = ''
      this.day = ''
      this.remainder = false
    },
  },
};


</script>

<style scoped>
input[type="text"] {
  padding: 12px;
  border-radius: 10px;
  margin-bottom: 10px;
  outline: none;
}

input.btn.btn-block {
  padding: 10px;
  background-color: #9292a8;
  border: navajowhite;
  border-radius: 10px;
  cursor: pointer;
}

form.add-form {
  width: 500px;
  margin: auto;
  margin-top: 26px;
}
</style>
