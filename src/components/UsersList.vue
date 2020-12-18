<template>
  <section>
    <b-table :data="users" :columns="columns">
      <b-table-column field="roles" label="Roles" centered v-slot="props">
        <span v-for="item in props.row.roles" class="tag mr-2" :key="item">
          {{item.role}}
        </span>
      </b-table-column>
    </b-table>
  </section>
</template>

<script>
import axios from 'axios';
import 'buefy/dist/buefy.css';

export default {
  data() {
    return {
      users: [],
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
        {
          field: 'email',
          label: 'Email',
          searchable: true,
        },
        {
          field: 'isActive',
          label: 'Active?',
          searchable: true,
        },
        {
          field: 'roles',
          label: 'Role',
          searchable: true,
        },
      ],
    };
  },
  mounted() {
    axios
      .get('http://localhost:9090/v1.0/users')
      .then((response) => {
        console.log(response.data);
        this.users = response.data;
        return null;
      });
  },
};
</script>
