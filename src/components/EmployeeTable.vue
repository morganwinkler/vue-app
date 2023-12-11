<template>
  <!-- file names and imports are PascalCase, but inside template is kebab-case -->
  <!-- template can only have one root child element -->
  <div id="employee-table">
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Richard Hendricks</td>
          <td>richard@piedpiper.com</td>
        </tr>
        <tr>
          <td>Bertram Gilfoyle</td>
          <td>gilfoyle@piedpiper.com</td>
        </tr>
        <tr>
          <td>Dinesh Chugtai</td>
          <td>dinesh@piedpiper.com</td>
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

<style scoped></style>
