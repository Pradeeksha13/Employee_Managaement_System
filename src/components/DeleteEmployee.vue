<template>
<div class="container mt-4">
  <h2>Delete Employee</h2>

  <table class="table table-bordered">
  <thead>
    <tr>
      <th>Name</th>
      <th>Department</th>
      <th>Action</th>
    </tr>
  </thead>

  <tbody>
    <tr v-for="e in list" :key="e.id">
      <td>{{ e.name }}</td>
      <td>{{ e.department }}</td>
      <td>
        <button class="btn btn-danger" @click="remove(e.id)">
          Delete
        </button>
      </td>
    </tr>
  </tbody>
</table>
</div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      api: "https://69e9b56655d62f34797ad254.mockapi.io/project1/api/v1/employees",
      list: []
    }
  },
  methods: {
    async fetch() {
      const res = await axios.get(this.api)
      this.list = res.data
    },
    async remove(id) {
      if (!confirm("Delete?")) return
      await axios.delete(`${this.api}/${id}`)
      this.fetch()
    }
  },
  mounted() {
    this.fetch()
  }
}
</script>