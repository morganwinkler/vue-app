<template>
  <div id="employee-form">
    <!-- @submit shorthand for v-on:submit, prevent is same as event.preventDefault() -->
    <form @submit.prevent="handleSubmit">
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
  // the methods object will contain all the custom methods created
  methods: {
    handleSubmit() {
      console.log("testing handleSubmit");
      // this.$emit('name-of-emitted-event', dataToPass)
      // this is how we pass data back up to App
      this.$emit("add:employee", this.employee);
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
</style>
