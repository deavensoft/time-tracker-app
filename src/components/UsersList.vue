<template>
  <div>
    <ul v-for="user in users" :key="user.id">
      <li> {{user.id}}, {{user.name}} </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'UsersList',
  data() {
    return {
      users: null,
    };
  },
  mounted() {
    axios
      .get('https://jsonplaceholder.typicode.com/users')
      .then((response) => {
        this.users = response.data;
        return null;
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
