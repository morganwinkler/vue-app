<template>
  <div id="employee-form">
    <!-- @submit shorthand for v-on:submit, prevent is same as event.preventDefault() -->
    <form @submit.prevent="handleSubmit">
      <label>Employee name</label>
      <!-- v-model is built in for updating an input value with an onchange event -->
      <input
        v-model="employee.name"
        type="text"
        :class="{ 'has-error': submitting && invalidName }"
        @focus="clearStatus"
        @keypress="clearStatus"
        ref="first"
      />
      <label>Employee Email</label>
      <input
        :class="{ 'has-error': submitting && invalidEmail }"
        v-model="employee.email"
        @focus="clearStatus"
        type="text"
      />
      <!-- v-if is a Vue conditional -->
      <p v-if="error && submitting" class="error-message">❗Please fill out all required fields</p>
      <p v-if="success" class="success-message">✅ Employee successfully added</p>
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "employee-form",
  data() {
    return {
      submitting: false,
      error: false,
      success: false,
      employee: {
        name: "",
        email: "",
      },
    };
  },
  // the methods object will contain all the custom methods created
  methods: {
    handleSubmit() {
      this.submitting = true;
      this.clearStatus();

      if (this.invalidName || this.invalidEmail) {
        this.error = true;
        return;
      }

      this.$emit("add:employee", this.employee);
      // focus the ref after submit
      this.$refs.first.focus();
      this.employee = {
        name: "",
        email: "",
      };
      this.error = false;
      this.success = true;
      this.submitting = false;
    },

    clearStatus() {
      this.success = false;
      this.error = false;
    },
  },

  computed: {
    invalidName() {
      return this.employee.name === "";
    },

    invalidEmail() {
      return this.employee.email === "";
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}

[class*="-message"] {
  font-weight: 500;
}

.error-message {
  color: #d33c40;
}

.success-message {
  color: #32a95d;
}
</style>
