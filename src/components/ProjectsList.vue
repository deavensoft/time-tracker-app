<template>
  <section>
    <b-table :data="projects" v-if="!selectedProject">
      <b-table-column
        field="id"
        label="ID"
        sortable
        centered
        v-slot="props">
        {{ props.row.id }}
      </b-table-column>
      <b-table-column
        field="name"
        label="Name"
        sortable
        centered
        v-slot="props">
        {{ props.row.name }}
      </b-table-column>
      <b-table-column
        field="description"
        label="Description"
        sortable
        centered
        v-slot="props">
        {{ props.row.description }}
      </b-table-column>
      <b-table-column
        field="isActive"
        label="Active?"
        sortable
        centered
        v-slot="props">
        {{ props.row.isActive }}
      </b-table-column>
      <b-table-column field="users" label="Users" centered v-slot="props">
        <span v-for="item in props.row.users" class="tag mr-2" :key="item.name">
          {{ item.email }}
        </span>
      </b-table-column>

      <b-table-column
        label="Detail"
        v-slot="props">
        <button @click="openProjectDetails(props.row)">Project</button>
      </b-table-column>
    </b-table>

    <ProjectDetail
      v-else
      :project="selectedProject"/>

    </section>
</template>

<script>
import axios from 'axios';
import 'buefy/dist/buefy.css';
import ProjectDetail from '@/components/ProjectDetail.vue';

export default {
  name: 'ProjectsList',
  components: {
    ProjectDetail,
  },
  data() {
    return {
      selectedProject: null,
      projects: [],
    };
  },
  methods: {
    openProjectDetails(project) {
      this.selectedProject = project;
      console.log('project');
    },
  },
  mounted() {
    axios
      .get('http://localhost:9090/v1.0/projects')
      .then((response) => {
        console.log(response.data);
        this.projects = response.data;
        return null;
      });
  },
};
</script>

<style scoped>

</style>
