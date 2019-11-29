<template>
  <div class="about">
    <h1>This is an about page</h1>
    <UsersTable msg="Welcome to Your Vue.js App"/>
  </div>
</template>


<script>
// @ is an alias to /src
import UsersTable from '@/components/UsersTable.vue'

export default {
  name: 'home',
  components: {
    UsersTable
  }
}
</script>