<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <div class="view">
        <div class="container">
          <Form @onSubmit="addTweet" />
          <TweetList :items="items" />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
import Form from "@/components/Form.vue";
import List from "@/components/List.vue";
export default {
  components: {
    TweetList: List,
    Form,
  },
  setup() {
    const items = ref([
      {
        id: 1,
        avatar: `https://avatars.dicebear.com/api/male/1.svg`,
        body: "body",
        likes: 12,
        date: new Date(Date.now()).toLocaleString(),
      },
    ]);

    const addTweet = (item) => items.value.push(item);

    // function addTweet(item) {
    //   items.value.push(item);
    // }

    return {
      items,
      addTweet,
    };
  },
};
// export default {
//   components: {
//     TweetList: List,
//     Form,
//   },
//   data() {
//     return {
//       items: [
//         {
//           id: 1,
//           avatar: `https://avatars.dicebear.com/api/male/1.svg`,
//           body: "body",
//           likes: 12,
//           date: new Date(Date.now()).toLocaleString(),
//         },
//       ],
//     };
//   },
//   methods: {
//     addTweet(item) {
//       this.items.push(item);
//     },
//   },
// };
</script>
<style></style>
