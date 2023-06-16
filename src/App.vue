<template>
  <ul>
    <learning-resource
      v-for="item in storedResuources"
      :key="item.id"
      :title="item.title"
      :description="item.description"
      :link="item.link"
    > </learning-resource>
  </ul>
</template>

<script>
import LearningResource from "./components/learning-recources/LearningResource.vue";
export default {
  components: {
    LearningResource,
  },
  data() {
    return {
      storedResuources: [
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
};
</script>
