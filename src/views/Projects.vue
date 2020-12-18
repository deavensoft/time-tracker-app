<template>
  <div class="projects">
    <ProjectsList></ProjectsList>
  </div>
</template>

<script>
import ProjectsList from '@/components/ProjectsList.vue';

export default {
  name: 'Projects',
  components: {
    ProjectsList,
  },
};
</script>
