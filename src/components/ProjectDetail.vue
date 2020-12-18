<template>
  <div>
  <b-field label="Name">
    <b-input v-model="project.name"></b-input>
  </b-field>

  <b-field label="Description">
    <b-input v-model="project.description"></b-input>
  </b-field>
  <b-field label="Active">
    <b-checkbox v-model="project.isActive"></b-checkbox>
  </b-field>
  <b-field>
    <span v-for="user in project.users" :key="user.id">
      {{user.firstName}}
    </span>
  </b-field>
  </div>
</template>

<script>

export default {
  name: 'ProjectDetail',
  props: ['project'],
};

</script>

<style scoped>

</style>
