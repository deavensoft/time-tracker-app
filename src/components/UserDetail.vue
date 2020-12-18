<template>
<div>
  <p>{{id}}</p>
  <p>{{firstName}}</p>
  <p>{{lastName}}</p>
  <p>{{email}}</p>
  <p v-for="role in roles" :key="role">{{role.role}}</p>
</div>
</template>

<script>
export default {
  name: 'UserDetail',
  props: ['id', 'firstName', 'lastName', 'email', 'roles'],
};
</script>

<style scoped>

</style>
