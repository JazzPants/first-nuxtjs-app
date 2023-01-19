<template>
  <main>
  <h1>Task Board</h1>
  <p>Create a list of tasks</p>

  <div class="create-new">
  <input type="text" v-model="newTask" placeHolder="Add a new task" @keypress.enter="addTask"/>
  <button @click="addTask">Add</button>
  </div>

  <div class="tasks">
    <!-- User made component, we call it "Task" here -->
  <Task v-for="(task, i) in $store.state.tasks" :key="i" :task="task" />
  {{ $store.state.tasks }}
  </div>

  </main>
</template>

<script>
export default {
  data(){
    return {
      newTask: ''
    }
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.$store.commit("ADD_TASK", this.newTask)
        this.newTask = '';
      }
    }
  }
};
</script>