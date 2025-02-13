<template>
  <div class="task-list-molecule">
    <TextAtom
      v-if="remainingTasks > 0"
      :text="'Faltam ' + remainingTasks + ' tarefa(s) para concluir.'"
      tag="p"
    />
    <TextAtom
      v-if="tasks.length === 0"
      :text="'Não há tarefas adicionadas!'"
      tag="p"
    />
    <TextAtom
      v-if="allCompleted && tasks.length !== 0"
      :text="'Todas as tarefas estão concluídas!'"
      tag="p"
    />

    <ul>
      <li v-for="task in tasks" :key="task.id">
        <TextAtom
          :text="task.text"
          :isCompleted="task.completed"
          @task-clicked="toggleTaskCompletion(task)"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import TextAtom from "../atoms/TextAtom.vue";

export default {
  name: "TaskRenderedMolecule",
  components: {
    TextAtom,
  },
  props: {
    tasks: {
      type: Array,
      required: true,
    },
    allCompleted: {
      type: Boolean,
      required: true,
    },
    remainingTasks: {
      type: Number,
      required: true,
    },
  },
  methods: {
    toggleTaskCompletion(task) {
      this.$emit("task-clicked", task);
    },
  },
};
</script>

<style scoped>
.task-list-molecule {
  margin-top: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 10px 0;
}

p {
  font-size: 1.1rem;
  color: #333;
}
</style>
