<template>
  <ul v-if="resources">
    <resource-item
      v-for="res in resources"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :url="res.url"
      :id="res.id"
    ></resource-item>
  </ul>
</template>

<script>
import ResourceItem from './ResourceItem.vue';

export default {
  components: {
    ResourceItem,
  },
  props: ['resources'],
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
