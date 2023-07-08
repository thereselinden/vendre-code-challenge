<template>
  <section class="contact-container">
    <h1>Contact</h1>

    <button @click="handleClick" class="go-back">&#8592;</button>
    <h4>
      Sending mail to: <span class="recipient">{{ id }}</span>
    </h4>
    <form @submit.prevent="handleSubmit">
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
      <button :disabled="!message" class="submit">Send message</button>
    </form>
  </section>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
      message: '',
    };
  },

  methods: {
    handleSubmit() {
      console.log('form submitted', this.id, this.message);
      this.message = '';
      history.back();
    },
    handleClick() {
      history.back();
    },
  },
};
</script>

<style>
.contact-container {
  max-width: 500px;
  margin: 0 auto;
}

.go-back {
  background: none;
  border: none;
  font-size: 2rem;
  color: #f49586;
  padding: 0;
  margin-bottom: 2rem;
  cursor: pointer;
}

.go-back:hover {
  scale: 1.3;
}

.recipient {
  font-weight: bold;
  color: #f49586;
}

form {
  display: flex;
  flex-direction: column;
  width: 100%;
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
