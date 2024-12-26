<template>
  <div>
    <label v-if="label" :for="inputId">{{ label }}</label>
    <input 
      :id="inputId" 
      :type="type" 
      :value="value" 
      @input="$emit('update:value', $event.target.value)"
      :placeholder="placeholder"
    />
  </div>
</template>

<script>
export default {
  name: 'BasicInput',
  props: {
    value: {
      type: String,
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: 'text'
    },
    placeholder: {
      type: String,
      default: ''
    }
  },
  computed: {
    inputId() {
      return this._uid; // Unique ID for input
    }
  }
};
</script>

<style scoped>
input {
  padding: 0.5em;
  font-size: 1em;
  border: 1px solid #ccc;
  border-radius: 4px;
}

label {
  display: block;
  margin-bottom: 0.5em;
  font-weight: bold;
}
</style>
