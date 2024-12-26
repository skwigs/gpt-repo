<template>
  <form @submit.prevent="handleSubmit">
    <BasicInput
      label="Name"
      v-model="form.name"
      placeholder="Enter your name"
    />
    <BasicInput
      label="Email"
      type="email"
      v-model="form.email"
      placeholder="Enter your email"
    />
    <div>
      <label for="message">Message</label>
      <textarea 
        id="message" 
        v-model="form.message" 
        placeholder="Enter your message"
      ></textarea>
    </div>
    <button type="submit">Submit</button>
  </form>
</template>

<script>
import BasicInput from './BasicInput.vue';

export default {
  name: 'ContactForm',
  components: {
    BasicInput
  },
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      }
    };
  },
  methods: {
    handleSubmit() {
      console.log('Form submitted:', this.form);
      alert('Thank you for your message!');
      this.form = { name: '', email: '', message: '' }; // Reset form
    }
  }
};
</script>

<style scoped>
form {
  max-width: 400px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 1em;
}

textarea {
  width: 100%;
  min-height: 100px;
  padding: 0.5em;
  font-size: 1em;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 0.7em;
  font-size: 1em;
  color: #fff;
  background-color: #007BFF;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>
