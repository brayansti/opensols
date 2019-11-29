<template>
  <div>
    <h1>
      TEST {{msg}}
    </h1>
    <div>
      {{users}}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'UsersTable',
  props: {
    msg: String
  },
  data(){
    return{
      users: null,
    }
  },
  methods: {
    getPosts () {
      // Parameters to get Data
      const parameters = {
        url: 'https://randomuser.me/api/',
        results: '1500'
      };
      axios.get(`${parameters.url}?results=${parameters.results}`)
        .then(response => {
          console.log(response);
          this.users = response.data.results
        })
        .catch(error => {
          console.log(error)
        });
    },
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
