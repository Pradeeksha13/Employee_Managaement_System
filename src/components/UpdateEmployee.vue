<template>
<div class="container mt-4">
  <h2>Update Employee</h2>

  <table class="table table-bordered">
  <thead>
    <tr>
      <th>Name</th>
      <th>Designation</th>
      <th>Department</th>
      <th>Salary</th>
      <th>Action</th>
    </tr>
  </thead>

  <tbody>
    <tr v-for="e in list" :key="e.id">
      <td>{{ e.name }}</td>
      <td>{{ e.designation }}</td>
      <td>{{ e.department }}</td>
      <td>{{ e.salary }}</td>
      <td>
        <button class="btn btn-warning" @click="edit(e)">Edit</button>
      </td>
    </tr>
  </tbody>
</table>
  <div v-if="editData.id" class="card p-3">
    <h4>Edit Employee</h4>

    <input v-model="editData.name" class="form-control mb-2" />
    <input v-model="editData.designation" class="form-control mb-2" />
    <input v-model="editData.department" class="form-control mb-2" />
    <input v-model="editData.salary" class="form-control mb-2" />

    <button class="btn btn-success" @click="update">Update</button>
  </div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      api: "https://69e9b56655d62f34797ad254.mockapi.io/project1/api/v1/employees",
      list: [],
      editData: {}
    }
  },
  methods: {
    async fetch() {
      const res = await axios.get(this.api)
      this.list = res.data
    },
    edit(e) {
      this.editData = { ...e }
    },
    async update() {
      await axios.put(`${this.api}/${this.editData.id}`, this.editData)
      alert("Updated!")
      this.editData = {}
      this.fetch()
    }
  },
  mounted() {
    this.fetch()
  }
}
</script>