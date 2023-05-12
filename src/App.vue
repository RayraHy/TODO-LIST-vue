<template>
  <div id="app">
    <h1>Tarefas</h1>
    <NewTaskVue @taskAdded="addTask" />
    <TaskGrid :tasks="tasks" @taskDeleted="deleteTask" @taskStateChanged="toggleTaskState" />
    
  </div>
</template>

<script>
import NewTaskVue from './components/NewTask.vue';
import TaskGrid from './components/TaskGrid.vue';

export default {
  components: {
    TaskGrid,
    NewTaskVue
  },
  data() {
    return {
      tasks: [
        {
          name: 'Lavar louça',
          pending: true
        },
        {
          name: 'Lavar roupa',
          pending: false
        },
      ]
    }
  },
  methods: {
    addTask(task) {
      const sameName = t => t.name === task.name
      const reallyNew = this.tasks.filter(sameName).length == 0;

      if(reallyNew) {
        this.tasks.push({
          name: task.name,
          pending: true
        });
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    toggleTaskState(index) {
      this.tasks[index].pending = !this.tasks[index].pending
    },
  }

}
</script>

<style>
  body {
    font-family: 'Lato', sans-serif;
    background: linear-gradient(to right, rgb(38, 22, 42), rgb(115, 67, 58));
    color: white;
  }

  #app {
    display: flex;
    flex: 1;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  #app h1 {
    margin-bottom: 5px;
    font-weight: 300;
    font-size: 3rem;
  }
</style>