<template>
  <!-- file names and imports are PascalCase, but inside template is kebab-case -->
  <!-- template can only have one root child element -->
  <div id="employee-table">
    <p v-if="employees.length < 1" class="empty-table">No employees</p>
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <!-- v-for is used to render list from an array -->
        <!-- vue also requires a unique identifier for looping, use the :key -->
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>
          <td>{{ employee.email }}</td>
          <td>
            <button>Edit</button>
            <button @click="$emit('delete:employee', employee.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "employee-table",
  // tells component it will be receiving props in the form of an array
  props: {
    employees: Array,
  },
};
</script>

<style scoped>
button {
  margin: 0 0.5rem 0 0;
}
</style>
