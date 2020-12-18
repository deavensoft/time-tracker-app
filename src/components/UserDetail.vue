<template>
<div>
    <b-field label="First name">
      <b-input v-model="user.firstName"></b-input>
    </b-field>

    <b-field label="Last name">
      <b-input v-model="user.lastName"></b-input>
    </b-field>
    <b-field label="Email"
             type="is-danger"
             message="This email is invalid">
      <b-input v-model="user.email"></b-input>
    </b-field>
    <b-field label="Active">
      <b-checkbox v-model="user.isActive"></b-checkbox>
    </b-field>
  <b-field>
    <b-select multiple native-size="3" v-model="user.roles">
      <option :value="{role: 'ADMIN'}">Admin</option>
      <option :value="{role: 'MANAGER'}">Manager</option>
      <option :value="{role: 'EMPLOYEE'}">Employee</option>
    </b-select>
  </b-field>

  <b-button type="is-primary" @click="save">Save</b-button>
  <b-button type="is-light" @click="cancel">Cancel</b-button>
</div>
</template>

<script>
export default {
  name: 'UserDetail',
  props: ['user'],
  methods: {
    save() {
      this.$emit('save', this.user);
    },
    cancel() {
      this.$emit('cancel');
    },
  },
};
</script>

<style scoped>

</style>
