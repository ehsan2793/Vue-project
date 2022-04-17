<template>
  <ul>
    <stored-resources :resources="storedResources"> </stored-resources>
  </ul>
</template>

<script>
import StoredResources from './components/learning-resources/SortedResources.vue';

export default {
  components: { StoredResources },
  data() {
    return {
      storedResources: [
        {
          id: 1,
          title: 'Offical guide',
          description: 'The offical Vue.js documentation ',
          link: 'http://vue.js.org',
        },
        {
          id: 2,
          title: 'Google search',
          description: 'Leanr to google',
          link: 'http://google.com',
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

body {
  margin: 0;
}
</style>
