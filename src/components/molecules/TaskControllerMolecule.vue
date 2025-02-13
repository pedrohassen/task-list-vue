<template>
  <div class="task-input-molecule">
    <!-- Título do Projeto -->
    <TextAtom :text="title" tag="h1" customClass="task-title" />

    <!-- Input para adicionar nova tarefa -->
    <InputAtom
      v-model="taskInput"
      placeholder="Inserir Tarefa"
      customClass="input-task"
    />

    <!-- Botões -->
    <div class="buttons">
      <ButtonAtom
        text="Adicionar Tarefa"
        @buttonClicked="addTask"
        customClass="add-button"
      />
      <ButtonAtom
        text="Deletar Lista"
        @buttonClicked="deleteList"
        customClass="delete-button"
      />
    </div>
  </div>
</template>

<script>
import TextAtom from "../atoms/TextAtom.vue";
import InputAtom from "../atoms/InputAtom.vue";
import ButtonAtom from "../atoms/ButtonAtom.vue";

export default {
  name: "TaskControllerMolecule",
  components: {
    TextAtom,
    InputAtom,
    ButtonAtom,
  },
  data() {
    return {
      title: "Lista de Tarefas",
      taskInput: "",
    };
  },
  methods: {
    addTask() {
      if (this.taskInput.trim() !== "") {
        this.$emit("add-task", this.taskInput); // Emitindo o evento "add-task"
        this.taskInput = ""; // Limpar o campo de input após adicionar
      }
    },
    deleteList() {
      this.$emit("delete-list"); // Emitir o evento para deletar a lista
    },
  },
};
</script>

<style scoped>
.task-input-molecule {
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  margin-bottom: 20px;
}

.input-task {
  margin-bottom: 10px;
  width: 60%;
}

.buttons {
  display: flex;
  justify-content: space-between;
  gap: 10px;
}

.add-button,
.delete-button {
  padding: 8px 16px;
  font-size: 16px;
  border-radius: 4px;
}

.delete-button {
  background-color: red;
  color: white;
}

.add-button {
  background-color: #4caf50;
  color: white;
}
</style>
