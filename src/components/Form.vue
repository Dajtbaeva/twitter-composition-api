<template>
  <form @submit.prevent="addTweet">
    <textarea
      v-model="body"
      required
      placeholder="Type your tweet here"
    ></textarea>
    <button class="btn btnTweet" type="submit">Post Tweet</button>
  </form>
</template>
<script>
import { ref } from "vue";
export default {
  emits: ["onSubmit"],
  setup(props, { emit }) {
    const body = ref("");

    const addTweet = () => {
      emit("onSubmit", {
        id: Math.round(Math.random() * 30),
        avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
        body: body.value,
        likes: 0,
        date: new Date(Date.now()).toLocaleString(),
      });
      body.value = "";
    };
    return { body, addTweet };
  },
};
// export default {
//   data() {
//     return {
//       body: "",
//     };
//   },
//   methods: {
//     addTweet() {
//       this.$emit("onSubmit", {
//         id: Math.round(Math.random() * 30),
//         avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
//         body: this.body,
//         likes: 0,
//         date: new Date(Date.now()).toLocaleString(),
//       });
//       this.body = "";
//     },
//   },
// };
</script>
