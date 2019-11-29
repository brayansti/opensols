<template>
  <div class="about">
    <h2>
      Desde acá puedes ver los usuarios
    </h2>
    <UsersTable />
  </div>
</template>


<script>
// @ is an alias to /src
import UsersTable from '@/components/UsersTable.vue'

export default {
  name: 'users',
  components: {
    UsersTable
  },
}
</script>