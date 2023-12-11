<template>
  <div id="app" class="small-container">
    <h1>Employees</h1>
    <!-- an attribute that begins with a colon will allow you to pass data -->
    <employee-table :employees="employees" />
    <!-- another syntax option -->
    <!-- <employee-table v-bind:employees="employees" /> -->
  </div>
</template>

<script>
// @ is used to reference the src folder & all imported components must be added to components folder
import EmployeeTable from "@/components/EmployeeTable.vue";

export default {
  name: "app",
  components: {
    EmployeeTable,
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: "Richard Hendricks",
          email: "richard@piedpiper.com",
        },
        {
          id: 2,
          name: "Bertram Gilfoyle",
          email: "gilfoyle@piedpiper.com",
        },
        {
          id: 3,
          name: "Dinesh Chugtai",
          email: "dinesh@piedpiper.com",
        },
      ],
    };
  },
};
</script>

<style>
button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 680px;
}
</style>
