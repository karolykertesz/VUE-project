<template>
  <base-card>
    <base-button @click="changeResource('stored-resources')" :mode="buttonColor"
      >Stored Resources</base-button
    >
    <base-button @click="changeResource('add-resource')" :mode="resButtonColor">
      Add Resources</base-button
    >
  </base-card>
  <component :is="currentResource"></component>
</template>

<script>
import StoredResources from './StoredResource.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      currentResource: 'stored-resource',
      resources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'Official Vue documetation',
          url: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google',
          url: 'https://google.com',
        },
      ],
    };
  },
  computed: {
    buttonColor() {
      const storedButton =
        this.currentResource === 'stored-resources' ? null : 'flat';
      return storedButton;
    },
    resButtonColor() {
      const resStoredButton =
        this.currentResource === 'add-resource' ? null : 'flat';
      return resStoredButton;
    },
  },
  provide() {
    return {
      resources: this.resources,
    };
  },

  methods: {
    changeResource(res) {
      console.log(res);
      this.currentResource = res;
    },
  },
};
</script>
