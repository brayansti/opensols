<template>
  <div class="about">
    <h1>
      Bienvenido, acá puedes consultar los usuarios
    </h1>
    <UsersTable />
  </div>
</template>


<script>
// @ is an alias to /src
import UsersTable from '@/components/UsersTable.vue'

export default {
  name: 'home',
  components: {
    UsersTable
  },
}
</script>