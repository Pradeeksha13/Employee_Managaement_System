<template>
<div class="container mt-4">
  <h2>Add Employee</h2>

  <form @submit.prevent="addEmployee" class="card p-3">
    <input v-model="emp.name" class="form-control mb-2" placeholder="Name" required />
    <input v-model="emp.designation" class="form-control mb-2" placeholder="Designation" required />
    <input v-model="emp.department" class="form-control mb-2" placeholder="Department" required />
    <input v-model="emp.salary" type="number" class="form-control mb-2" placeholder="Salary" required />

    <button class="btn btn-primary">Add Employee</button>
  </form>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: "PostComp",
  data() {
    return {
      api: "https://69e9b56655d62f34797ad254.mockapi.io/project1/api/v1/employees",
      emp: {
        name: "",
        designation: "",
        department: "",
        salary: ""
      }
    }
  },
  methods: {
    async addEmployee() {
      try {
        await axios.post(this.api, this.emp)
        alert("Employee Added!")
        this.emp = { name: "", designation: "", department: "", salary: "" }
      } catch (err) {
        console.error(err)
      }
    }
  }
}
</script>