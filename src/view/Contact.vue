<template>
  <button @click="handleClick">Back home</button>
  <form @submit.prevent="handleSubmit">
    <label for="emailTo">Send to:</label>
    <input type="email" id="emailTo" required v-model="emailTo" />
    <label for="message">Message:</label>
    <textarea
      name="message"
      id="message"
      cols="30"
      rows="10"
      minlength="6"
      required
      v-model="message"
    ></textarea>
    <button :disabled="!emailTo || !message" class="submit">
      Send message
    </button>
  </form>
  email: {{ emailTo }}
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
      emailTo: '',
      message: '',
    };
  },

  methods: {
    handleSubmit() {
      console.log('form submitted', this.emailTo, this.message);
      (this.emailTo = ''), (this.message = '');
    },
    handleClick() {
      history.back();
    },
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
}

label {
  font-size: 0.8rem;
}

input,
textarea {
  border: none;
  margin-bottom: 1rem;
  font-size: 1rem;
}

input {
  border-bottom: 1px solid #f49586;
}

textarea {
  border: 1px solid #f49586;
  font-family: inherit;
}

.submit {
  padding: 0.6rem;
  margin-top: 1rem;
  border: none;
  background: #f49586;
  color: #fff;
  border-radius: 5px;
  width: 100%;
  text-transform: uppercase;
  cursor: pointer;
}
</style>
