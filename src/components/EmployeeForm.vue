<template>
  <div id="employee-form">
    <form>
      <label>Employee name</label>
      <!-- v-model is built in for updating an input value with an onchange event -->
      <input v-model="employee.name" type="text" />
      <label>Employee Email</label>
      <input v-model="employee.email" type="text" />
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "employee-form",
  data() {
    return {
      employee: {
        name: "",
        email: "",
      },
    };
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
</style>
