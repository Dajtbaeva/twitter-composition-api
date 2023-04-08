<template>
  <select v-model="sortBy">
    <option value="date">Sort by date</option>
    <option value="likes">Sort by likes</option>
  </select>
  <ul>
    <Tweet v-for="item in sortedList" :key="item.id" :item="item"></Tweet>
  </ul>
</template>
<script>
import Tweet from "@/components/Tweet.vue";
import { ref, computed } from "vue";

export default {
  components: { Tweet },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  setup({ items }) {
    const sortBy = ref("date");
    const sortedList = computed(() => {
      return items.sort((a, b) => {
        if (a[sortBy.value] > b[sortBy.value]) return -1;
        if (a[sortBy.value] < b[sortBy.value]) return 1;
        // new tweets and tweets with more likes at the top
      });
    });
    return { sortBy, sortedList };
  },
};
</script>
<style scoped></style>
