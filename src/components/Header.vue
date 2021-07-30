<template>
  <header>
    <div class="container">
      <div class="header-content">
        <router-link :to="{ name: 'Home' }"
          ><h1>{{ title }}</h1></router-link
        >
        <nav :class="{ nav: open }">
          <ul
            v-for="list in lists"
            :key="list.index"
            :style="{ background: list.fav }"
          >
            <li>{{ list.author }}</li>
            <li>{{ list.book }}</li>
            <li class="content">{{ list.content }}</li>
          </ul>
          <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link :to="{ name: 'About' }">About</router-link>
          </div>
        </nav>
        <div
          @click="openNav"
          class="toggle"
          :class="{ change: open }"
          ref="list"
        >
          <div></div>
          <div></div>
          <div></div>
        </div>
      </div>
    </div>
  </header>
  <div class="bg-change">
    <div class="container">
      <slot name="awe-one"></slot>
      <button @click="changeBg">Toggle background</button>
      <slot name="awe-two"></slot>
    </div>
  </div>
</template>
<script>
export default {
  name: "Header",
  props: ["lists", "title"],
  data() {
    return {
      open: false,
    };
  },
  methods: {
    openNav() {
      this.open = !this.open;
    },
    changeBg() {
      this.$refs.list.classList.toggle("bg");
    },
  },
};
</script>
<style scoped>
header {
  background: #f4f4f4;
  box-shadow: 1px 1px 2px black;
  position: fixed;
  width: 100%;
}
.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
}
.header-content nav {
  background: #f4f4f4;
  height: 100vh;
  width: 30%;
  padding: 1rem;
  transition: left 0.4s ease-in-out;
  position: fixed;
  left: -100%;
  top: 50px;
}
.header-content ul {
  list-style-type: none;
  background: #f4f4f4;
  margin: 0.5rem 0;
  padding: 0.5rem;
  border-radius: 5px;
  transition: all 0.4s ease-in-out;
  position: relative;
  cursor: pointer;
}
.header-content ul:hover .content {
  opacity: 1;
  height: 100%;
}
.header-content .nav {
  left: 0;
}
.toggle > div {
  background: #000;
  width: 30px;
  height: 3px;
  margin: 0 0 0.2rem 0;
  transition: 0.4s ease;
  cursor: pointer;
}
.change.toggle > div:nth-child(1) {
  transform: translate(1px, 5px) rotate(45deg);
}
.change.toggle > div:nth-child(2) {
  opacity: 0;
}
.change.toggle > div:nth-child(3) {
  transform: translate(0px, -7px) rotate(-45deg);
}
.content {
  position: absolute;
  top: 0;
  left: 0;
  height: 0;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: burlywood;
  border-radius: 5px;
  opacity: 0;
  transition: all 0.4s ease-in-out;
}
.bg {
  background: yellow;
}
.bg-change {
  padding-top: 5rem;
}
#nav {
  padding: 30px;
  text-align: center;
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
}
#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
