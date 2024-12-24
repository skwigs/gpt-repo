<template>
  <button 
    :class="buttonClass" 
    :disabled="disabled" 
    @click="onClick">
    <slot />
  </button>
</template>

<script>
export default {
  name: "ButtonComponent",
  props: {
    type: {
      type: String,
      default: "button",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    variant: {
      type: String,
      default: "primary",
    },
  },
  computed: {
    buttonClass() {
      return [
        "btn",
        `btn-${this.variant}`,
        { "btn-disabled": this.disabled }
      ];
    },
  },
  methods: {
    onClick(event) {
      if (!this.disabled) {
        this.$emit("click", event);
      }
    },
  },
};
</script>

<style scoped>
.btn {
  padding: 0.5em 1em;
  font-size: 1rem;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
.btn-primary {
  background-color: #007bff;
  color: #fff;
}
.btn-secondary {
  background-color: #6c757d;
  color: #fff;
}
.btn-disabled {
  background-color: #e0e0e0;
  color: #aaa;
  cursor: not-allowed;
}
</style>
