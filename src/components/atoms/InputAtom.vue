<template>
  <input
    :value="value"
    :placeholder="placeholder"
    :style="customStyle"
    :class="customClass"
    @input="handleInput"
  />
</template>

<script>
export default {
  name: "InputAtom",
  props: {
    value: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
      default: "",
    },
    customStyle: {
      type: Object,
      default: () => ({}),
    },
    customClass: {
      type: String,
      default: "",
    },
  },
  methods: {
    handleInput(event) {
      this.$emit("input", event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  width: 100%;
  margin: 5px 0;
}

input:focus {
  outline: none;
  border-color: #4caf50;
}
</style>
