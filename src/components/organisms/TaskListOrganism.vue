<template>
  <div class="task-organism">
    <TaskControllerMolecule
      @add-task="handleTaskAdded"
      @delete-list="handleListDeleted"
    />

    <TaskRenderedMolecule
      :tasks="tasks"
      :remainingTasks="remainingTasks"
      :allCompleted="allCompleted"
      @task-clicked="handleTaskCompletionToggle"
    />
  </div>
</template>

<script>
import TaskControllerMolecule from "../molecules/TaskControllerMolecule.vue";
import TaskRenderedMolecule from "../molecules/TasksRenderedMolecule.vue";

export default {
  name: "TaskListOrganism",
  components: {
    TaskControllerMolecule,
    TaskRenderedMolecule,
  },
  data() {
    return {
      tasks: [],
    };
  },
  computed: {
    allCompleted() {
      return this.tasks.every((task) => task.completed);
    },
    remainingTasks() {
      return this.tasks.filter((task) => !task.completed).length;
    },
  },
  methods: {
    // Handler para adicionar tarefa à lista
    handleTaskAdded(taskText) {
      const newTask = {
        id: Date.now(),
        text: taskText,
        completed: false,
      };
      this.tasks.push(newTask);
    },

    // Handler para deletar todas as tarefas
    handleListDeleted() {
      this.tasks = [];
    },

    // Handler para marcar tarefa como completada ou não
    handleTaskCompletionToggle(task) {
      task.completed = !task.completed;
    },
  },
};
</script>

<style scoped>
.task-organism {
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
}
</style>
