<template>
  <div>
    <Header @toggle-button="togleHandler" title="Task Tracker " />
    <div v-if="showAddTask">
      <Add-task @new-task="addTaskHandler" />
    </div>
    <div :key="task.id" v-for="task in tasks">
      <Tasks
        @toggle-remainder="toggleReaminder"
        @delete-item="deleteItemHandler"
        :task="task"
      />
    </div>
  </div>
</template>

<script>
import AddTask from "./components/AddTask.vue";
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
export default {
  name: "App",
  components: { Header, Tasks, AddTask },
  data() {
    return {
      tasks: [],
      showAddTask: false,
      
    };
  },

  methods: {
    togleHandler(){
      this.showAddTask = !this.showAddTask
    },

    addTaskHandler(task) {
      this.tasks = [...this.tasks, task];
    },

    deleteItemHandler(id) {
      if (confirm("Are you sure ?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReaminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, remainder: !task.remainder } : task
      );
    },
  },

  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointmenty",
        day: "March 1st at 2:30px",
        remainder: false,
      },
      {
        id: 2,
        text: "Doctors Janina",
        day: "March 1st at 2:30px",
        remainder: true,
      },
      {
        id: 3,
        text: "Doctors Kibabe korbo",
        day: "March 1st at 2:30px",
        remainder: false,
      },
      {
        id: 4,
        text: "Doctors Kibabe korbo",
        day: "March 1st at 2:30px",
        remainder: false,
      },
    ];
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
* {
  margin: 0px;
  padding: 0px;
}
</style>
