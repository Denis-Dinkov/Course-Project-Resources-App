<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resources</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";

export default {
  components: {
    AddResource,
    StoredResources,
  },
  data() {
    return {
      selectedTab: "stored-resources",
      StoredResources: [
        {
          id: "official-guide",
          title: "Official  Guide",
          description: "The official Vue.js documentation",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          description: "Learn to Google",
          link: "https://google.com",
        },
      ],
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title,description,url){
      const newResource = {
        id: new Date().toISOString,
        title,
        description,
        url,
      }
      this.StoredResources.unshift(newResource),
      this.selectedTab = 'stored-resources'
    }
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === "stored-resources" ? null : "flat";
    },
    addResButtonMode() {
      return this.selectedTab === "add-resource" ? null : "flat";
    },

  },
  provide() {
    return {
      resources: this.StoredResources,
      addResource: this.addResource,
    };
  },
};
</script>
