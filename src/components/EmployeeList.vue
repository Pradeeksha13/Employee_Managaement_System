<template>
<div class="container mt-4">
  <h2>Employee List</h2>

  <table class="table table-bordered table-striped">
    <thead class="table-dark">
      <tr>
        <th>ID</th>
        <th>Name</th>
        <th>Designation</th>
        <th>Department</th>
        <th>Salary</th>
      </tr>
    </thead>

    <tbody>
      <tr v-for="e in list" :key="e.id">
        <td>{{ e.id }}</td>
        <td>{{ e.name }}</td>
        <td>{{ e.designation }}</td>
        <td>{{ e.department }}</td>
        <td>{{ e.salary }}</td>
      </tr>
    </tbody>
  </table>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: "EmployeeList",
  data() {
    return {
      api: "https://69e9b56655d62f34797ad254.mockapi.io/project1/api/v1/employees",
      list: []
    }
  },
  async mounted() {
    const res = await axios.get(this.api)
    this.list = res.data
  }
}
</script>