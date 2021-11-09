<template>
  <base-card>
    <base-button @click="changeResource('stored-recources')"
      >Stored Resources</base-button
    >
    <base-button @click="changeResource('add-recource')">
      Add Resources</base-button
    >
  </base-card>
  <component :is="currentResource"></component>
</template>

<script>
import StoredResource from './StoredResource.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    StoredResource,
    AddResource,
  },
  data() {
    return {
      currentResource: 'stored-recources',
    };
  },
  methods: {
    changeResource(res) {
      this.currentResource = res;
    },
  },
};
</script>
