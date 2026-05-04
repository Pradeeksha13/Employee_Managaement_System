<template>
<div class="container">
  <h1 class="text-center mt-3">Employee Management System</h1>

  <PostComp />
  <EmployeeList />
  <UpdateEmployee />
  <DeleteEmployee />
</div>
</template>

<script>
import PostComp from './components/PostComp.vue'
import EmployeeList from './components/EmployeeList.vue'
import UpdateEmployee from './components/UpdateEmployee.vue'
import DeleteEmployee from './components/DeleteEmployee.vue'

export default {
  components: {
    PostComp,
    EmployeeList,
    UpdateEmployee,
    DeleteEmployee
  }
}
</script>