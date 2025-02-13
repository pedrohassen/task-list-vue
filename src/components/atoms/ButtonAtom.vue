<template>
  <button
    :class="buttonClass"
    :style="customStyle"
    @click="handleClick"
    :disabled="disabled"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "ButtonAtom",
  props: {
    text: {
      type: String,
      required: true,
    },
    customStyle: {
      type: Object,
      default: () => ({}),
    },
    customClass: {
      type: String,
      default: "",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    type: {
      type: String,
      default: "button",
    },
  },
  computed: {
    buttonClass() {
      return `button ${this.customClass}`;
    },
  },
  methods: {
    handleClick() {
      if (!this.disabled) {
        this.$emit("buttonClicked"); // Agora emitimos "buttonClicked"
        console.log("Botão clicado");
      }
    },
  },
};
</script>

<style scoped>
.button {
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 4px;
  cursor: pointer;
  border: none;
  transition: background-color 0.3s ease;
}

.button:focus {
  outline: none;
}

.button:disabled {
  cursor: not-allowed;
  background-color: #e0e0e0;
}

.button:hover:not(:disabled) {
  background-color: #45a049;
}
</style>
