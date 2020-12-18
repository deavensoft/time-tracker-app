<template>
  <section>
    <b-table :data="users" v-if="!selectedUser">
      <b-table-column
        @click="openUserDetails(props.row)"
        field="id"
        label="ID"
        sortable
        centered
        v-slot="props">
        {{ props.row.id }}
      </b-table-column>
      <b-table-column
        field="firstName"
        label="First Name"
        sortable
        centered
        v-slot="props">
        {{ props.row.firstName }}
      </b-table-column>
      <b-table-column
        field="lastName"
        label="Last Name"
        sortable
        centered
        v-slot="props">
        {{ props.row.lastName }}
      </b-table-column>
      <b-table-column
        field="email"
        label="Email"
        sortable
        centered
        v-slot="props">
        {{ props.row.email }}
      </b-table-column>
      <b-table-column
        field="isActive"
        label="Active?"
        sortable
        centered
        v-slot="props">
        {{ props.row.isActive }}
      </b-table-column>
      <b-table-column field="roles" label="Roles" centered v-slot="props">
        <span v-for="item in props.row.roles" class="tag mr-2" :key="item.role">
          {{ item.role }}
        </span>
      </b-table-column>

      <b-table-column
        label="Detail"
        v-slot="props">
        <button @click="openUserDetails(props.row)">User</button>
      </b-table-column>
    </b-table>

    <UserDetail v-else
                :user="selectedUser"></UserDetail>
  </section>


</template>

<script>
import axios from 'axios';
import 'buefy/dist/buefy.css';
import UserDetail from '@/components/UserDetail.vue';

export default {
  components: {
    UserDetail,
  },
  data() {
    return {
      selectedUser: null,
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
  methods: {
    openUserDetails(user) {
      this.selectedUser = user;
      console.log('User', user);
    },
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
