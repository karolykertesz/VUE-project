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
      addResources: this.addResources,
      remove: this.removeResourse,
    };
  },

  methods: {
    changeResource(res) {
      this.currentResource = res;
    },
    addResources(res) {
      const { title, desc, url } = res;
      const newResourse = {
        id: new Date().toISOString(),
        title,
        description: desc,
        url,
      };

      this.resources.unshift(newResourse);
      this.currentResource = 'stored-resources';
    },
    removeResourse(id) {
      const index = this.resources.findIndex((el) => el.id === id);
      this.resources.splice(index, 1);
    },
  },
};
</script>
