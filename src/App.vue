<template>
  <the-header title="Learn Vue"></the-header>
  <the-resource></the-resource>
</template>
<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResource from './components/learning-resources/TheResource.vue';
export default {
  methods: {
    removeRecource(id) {
      this.resources = this.resources.filter((item) => item.id !== id);
    },
  },
  components: {
    TheHeader,
    TheResource,
  },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}
li {
  list-style-type: none;
}
body {
  margin: 0;
}
</style>
