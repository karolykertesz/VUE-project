<template>
  <the-header title="Learn Vue"></the-header>
</template>
<script>
import TheHeader from './components/layouts/TheHeader.vue';
export default {
  methods: {
    removeRecource(id) {
      this.resources = this.resources.filter((item) => item.id !== id);
    },
  },
  components: {
    TheHeader,
  },
  data() {
    return {
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
