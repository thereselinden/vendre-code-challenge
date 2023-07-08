<template>
  <h1>Employees</h1>
  <section class="employee-list">
    <article
      v-for="employee in employees"
      :key="employee.id"
      class="employee-card"
    >
      <Card :employee="employee" />
    </article>
  </section>
</template>

<script>
import Card from '../components/Card.vue';

export default {
  components: {
    Card,
  },
  data() {
    return {
      employees: null,
      page: 1,
    };
  },
  async mounted(page) {
    // FUNKAR INTE, PAGE = UNDEFINED
    console.log('page', page);
    const query = JSON.stringify(page);
    const url = `https://reqres.in/api/users?page=${query}`;
    console.log('url', url);
    try {
      const response = await fetch(`https://reqres.in/api/users`);
      const { data: employees } = await response.json();
      this.employees = employees;
    } catch (err) {
      console.log(err);
    }
  },
};
</script>

<style>
.employee-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  justify-items: center;
}

.employee-card {
  width: 100%;
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

@media (min-width: 668px) {
  .employee-list {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (min-width: 1024) {
  .employee-list {
    grid-template-columns: repeat(4, 1fr);
  }
}
</style>
