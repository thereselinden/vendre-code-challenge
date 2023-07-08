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
  <div class="pagination">
    <a @click="pagination(1)">1</a>
    <a @click="pagination(2)">2</a>
  </div>
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
  methods: {
    async fetchEmployees() {
      const query = JSON.stringify(this.page);
      const url = `https://reqres.in/api/users?page=${query}`;
      try {
        const response = await fetch(url);
        const { data: employees } = await response.json();
        this.employees = employees;
      } catch (err) {
        console.log(err);
      }
    },

    pagination(num) {
      this.page = num;
      this.fetchEmployees();
    },
  },

  async mounted() {
    await this.fetchEmployees();
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

.pagination {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
  gap: 1rem;
  cursor: pointer;
}

@media (min-width: 668px) {
  .employee-list {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>
