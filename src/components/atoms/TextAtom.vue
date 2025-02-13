<template>
  <component :is="tag" :class="textClass" @click="handleClick">
    {{ text }}
  </component>
</template>

<script>
export default {
  name: "TextAtom",
  props: {
    text: {
      type: String,
      required: true,
    },
    isCompleted: {
      type: Boolean,
      default: false,
    },
    customStyle: {
      type: Object,
      default: () => ({}),
    },
    customClass: {
      type: String,
      default: "",
    },
    tag: {
      type: String,
      default: "p",
    },
  },
  computed: {
    textClass() {
      return {
        completed: this.isCompleted,
        [this.customClass]: this.customClass,
      };
    },
  },
  methods: {
    handleClick() {
      // Emitindo o evento task-clicked ao invés de click
      this.$emit("task-clicked");
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
  color: gray;
}
</style>
