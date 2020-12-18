<template>
<div>
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
  <b-field>
    <b-select multiple native-size="3" v-model="user.roles">
      <option :value="{role: 'ADMIN'}">Admin</option>
      <option :value="{role: 'MANAGER'}">Manager</option>
      <option :value="{role: 'EMPLOYEE'}">Employee</option>
    </b-select>
  </b-field>
  <!--    <b-field label="Password"-->
  <!--      type="is-warning"-->
  <!--    :message="['Password is too short', 'Password must have at least 8 characters']">-->
  <!--      <b-input value="123" type="password" maxlength="30"></b-input>-->
  <!--    </b-field>-->


<!--  <p>{{id}}</p>-->
<!--  <p>{{firstName}}</p>-->
<!--  <p>{{lastName}}</p>-->
<!--  <p>{{email}}</p>-->
<!--  <p v-for="role in roles" :key="role">{{role.role}}</p>-->
</div>
</template>

<script>
export default {
  name: 'UserDetail',
  props: ['user'],
};
</script>

<style scoped>

</style>
