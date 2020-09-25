<template>
  <div class="users">
    <UsersList/>
  </div>
</template>

<script>
import UsersList from '@/components/UsersList.vue';

export default {
  name: 'Users',
  components: {
    UsersList,
  },
};
</script>
