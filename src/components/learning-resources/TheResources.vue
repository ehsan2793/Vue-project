<template>
  <base-card>
    <base-button
      @click="setSelectedTab('StoredResources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('AddResource')" :mode="AddResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './SortedResources.vue';
import AddResource from './AddResource.vue';
export default {
  components: { StoredResources, AddResource },
  data() {
    return {
      selectedTab: 'StoredResources',
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
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'StoredResources' ? null : 'flat';
    },
    AddResButtonMode() {
      return this.selectedTab === 'AddResource' ? null : 'flat';
    },
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      (this.selectedTab = 'StoredResources'),
        this.storedResources.unshift({
          id: Math.random() * 1000,
          title,
          description,
          link: url,
        });
    },
    removeResource(id) {
      console.log('me');
     console.log(this.storedResources);
     console.log(id);
     const index = this.storedResources.findIndex(item => item.id === id)

      // const indexItem = this.storedResources.findIndex();

      // console.log(indexItem);
      console.log('me2');
      this.storedResources.splice(index, 1);
    },
  },
};
</script>
