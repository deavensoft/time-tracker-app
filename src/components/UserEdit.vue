<template>
  <div>
    <section v-for="user in users" :key="user.id">
      <b-field label="First name">
        <b-input :value="user.firstName"></b-input>
      </b-field>

      <b-field label="Last name">
        <b-input :value="user.lastName"></b-input>
      </b-field>
      <b-field label="Email"
               type="is-danger"
               message="This email is invalid">
        <b-input :value="user.email"></b-input>
      </b-field>
      <b-field label="Active">
        <b-checkbox :value="user.isActive"></b-checkbox>
      </b-field>
      <b-field label="Password"
               type="is-warning"
               :message="['Password is too short', 'Password must have at least 8 characters']">
        <b-input value="123" type="password" maxlength="30"></b-input>
      </b-field>
    </section>
  </div>
</template>

<script>
import axios from 'axios';

import Vue from 'vue';
import Buefy from 'buefy';
import 'buefy/dist/buefy.css';

Vue.use(Buefy);

export default {
  name: 'UsersList',
  data() {
    return {
      users: null,
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
