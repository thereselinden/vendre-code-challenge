<template>
  <img
    :src="employee.avatar"
    :alt="employee.first_name"
    class="employee-avatar"
  />
  <h2>{{ employee.first_name }} {{ employee.last_name }}</h2>
  <router-link
    :to="{
      name: 'Contact',
      params: { id: employee.email },
    }"
  >
    <button class="contact-employee-btn">Contact</button>
  </router-link>
</template>

<script setup>
const props = defineProps(['employee']);
</script>

<style>
.employee-avatar {
  border-radius: 50%;
  border: 0.3rem solid#F49586;
}
.contact-employee-btn {
  padding: 0.4rem;
  margin-top: 0.3rem;
  border: none;
  background: #f49586;
  color: #fff;
  border-radius: 5px;
  width: 100%;
  text-transform: uppercase;
  cursor: pointer;
}
</style>
