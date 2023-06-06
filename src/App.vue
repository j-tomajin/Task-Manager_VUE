<script>
  import Header from './components/Header.vue';
  import Tasks from './components/Tasks.vue';
  import AddTask from './components/AddTask.vue';

  export default {
    name: 'App',
    components: {
      Header,
      Tasks,
      AddTask,
    },

    data() {
      return {
        tasks: [],
        showAddTask: false,
      }
    },

    methods: {
      newTask(task) {
        this.tasks = [...this.tasks, task]
      },

      toggleReminder(id) {
        this.tasks = this.tasks.map((task) => 
          task.id === id ? { ...task, reminder: !task.reminder } : task )
      },

      deleteTask(id) {
        if(confirm('Are you sure?')) {
          this.tasks = this.tasks.filter((task) => task.id !== id)
        }
      },

      toggleAddTask() {
        this.showAddTask = !this.showAddTask
      }
    },

    created() {
      this.tasks = []
    }
  }
</script>

<template>
  <Header 
    @toggle-add-task="toggleAddTask"
    :showAddTask="showAddTask"
    text="Task Manager" />

  <AddTask 
    @new-task="newTask"
    v-if="showAddTask"
  />

  <Tasks 
    @toggle-reminder="toggleReminder"
    @delete-task="deleteTask"
    :tasks="tasks"
  />
</template>

