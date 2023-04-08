<template>
  <ul>
    <Tweet v-for="item in items" :key="item.id" :item="item"></Tweet>
  </ul>
</template>
<script>
import Tweet from "@/components/Tweet.vue";

export default {
  components: { Tweet },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped></style>
