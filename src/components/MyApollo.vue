<template>
  <div class="my-apollo">
    <h1>{{ msg }}</h1>
    <div class="user-info">
      <table>
        <thead>
          <tr>
            <th>username</th>
            <th>email</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user.id">
            <td>{{user.username}}</td>
            <td>{{user.email}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag';

export default {
  name: 'MyApollo',
  props: {
    msg: String
  },
  apollo: {
    users: gql`{
              users 
              {
                id
                username
                email
              }}`
  },
  data() {
    return {
      users: [] 
    }
  }
}
</script>

<style scoped>
.user-info {
  display: flex;
  justify-content: center;
}

table {
  table-layout: fixed;
  width: 80%;
  border: 2px solid grey;
  border-collapse: collapse;
  letter-spacing: 1px;
}

thead th {
  border: 1px solid grey;
}


tbody {
  text-align: left;
}

tbody tr:nth-child(even) {
  background: #eaeaea;
}

tbody tr td {
  border-right: 1px solid grey;
}

th, td {
  padding: 5px 10px;
}

</style>
