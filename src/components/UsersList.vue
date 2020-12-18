<template>
  <section>
    <b-table :data="users" :columns="columns"></b-table>
  </section>
</template>

<script>
import axios from 'axios';
import 'buefy/dist/buefy.css';

export default {
  data() {
    return {
      users: null,
      columns: [
        {
          field: 'id',
          label: 'ID',
          width: '100',
          numeric: true,
          searchable: true,
        },
        {
          field: 'firstName',
          label: 'First Name',
          searchable: true,
        },
        {
          field: 'lastName',
          label: 'Last Name',
          searchable: true,
        },
      ],
    };
  },
  mounted() {
    axios
      .get('http://localhost:8080/v1.0/users')
      .then((response) => {
        console.log(response.data);
        this.users = response.data;
        return null;
      });
  },
};
</script>
