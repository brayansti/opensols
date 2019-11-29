<template>
  <div>
    <vue-good-table
      :columns="columns"
      :rows="rows"
      :search-options="{enabled: true}"
      :isLoading="tableLoading"
      >
    </vue-good-table>
    <!-- <h1> TEST </h1> -->
  </div>
</template>

<script>
import axios from "axios";
import { VueGoodTable } from 'vue-good-table';
import 'vue-good-table/dist/vue-good-table.css'

export default {
  name: 'UsersTable',
  data(){
    return{
      tableLoading: true,
      users: null,
      columns: [
        {
          label: 'Edad',
          field: 'old',
          type: 'number',
        },
        {
          label: 'Email',
          field: 'email',
        },
        {
          label: 'Nombre',
          field: 'name',
        },
        {
          label: 'Ubicación',
          field: 'location',
        },
        {
          label: 'Telefono',
          field: 'phone',
          type: 'number',
        },
      ],
      rows: [],
    }
  },
  components: {
    VueGoodTable
  },
  methods: {
    getPosts () {
      // Parameters to get Data
      const parameters = {
        url: 'https://randomuser.me/api/',
        results: '300'
      };
      axios.get(`${parameters.url}?results=${parameters.results}`)
        .then(response => {
          this.users = response.data.results
          this.printRows();
          this.tableLoading = false;
          console.log(response.data.results);
        })
        .catch(error => {
          console.log(error)
        });
    },
    printRows() {
      for (let index = 0; index < this.users.length; index++) {
        this.rows.push(
          {
            old: this.users[index].dob.age,
            email: this.users[index].email,
            name: `${this.users[index].name.title} ${this.users[index].name.first} ${this.users[index].name.last}`,
            location: this.users[index].location.city,
            phone: this.users[index].cell,
          }
        )
      }
    }
  },
  created () {
    this.getPosts();
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
