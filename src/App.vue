<template>
  <Header :lists="lists" :title="title">
    <template v-slot:awe-one>
      <p>I am awesome</p>
    </template>
    <template v-slot:awe-two>
      <p>I am more awesome</p>
    </template>
  </Header>
  <router-view />
</template>

<script>
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: { Header },
  data() {
    return {
      title: "Blade",
      lists: [
        {
          id: 1,
          author: "Blade",
          book: "Butterfly Jelly",
          content: "lorem ipsum dorlo kosiy",
          fav: "#dddddd",
        },
        {
          id: 2,
          author: "Bladeress",
          book: "Fish Jelly",
          content: "lorem ipsum dorlo kosiy",
          fav: "#ffffff",
        },
        {
          id: 3,
          author: "Bladant",
          book: "Butterfly Jelly",
          content: "lorem ipsum dorlo kosiy",
          fav: "#dddddd",
        },
      ],
    };
  },
  methods: {},
};
</script>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.container {
  width: 90%;
  margin: auto;
  overflow: hidden;
}
a {
  text-decoration: none;
  color: black;
}
@media screen and (min-width: 1000px) {
  .container {
    width: 980px;
  }
}
@media screen and (min-width: 1200px) {
  .container {
    width: 1100px;
  }
}
</style>
