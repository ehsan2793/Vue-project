<template>
  <base-card>
    <base-button
      @click="setSelectedTab('StoredResources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('AddResource')"
     :mode="AddResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
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
  computed:{
      storedResButtonMode(){
          return this.selectedTab === 'StoredResources' ? null : 'flat'
      },
      AddResButtonMode(){
          return this.selectedTab === 'AddResource' ? null : 'flat'
      }
  },
  provide() {
    return {
      resources: this.storedResources,
    };
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>
