<template>
  <teleport to=".awesome">
    <div class="container">
      <p>Blade is very awesome</p>
    </div>
  </teleport>
  <Form />
</template>

<script>
import Form from "../components/formHandling.vue";
export default {
  name: "Home",
  components: { Form },
  data() {
    return {};
  },
  methods: {},
  beforeCreate() {
    console.log("Before Create");
  },
  created() {
    console.log("Created");
  },
  beforeMount() {
    console.log("Before Mount");
  },
  mounted() {
    console.log("Mounted");
  },
  beforeUpdate() {
    console.log("Before Update");
  },
  updated() {
    console.log("Updated");
  },

  beforeUnmount() {
    console.log("Before Unmount");
  },
  unmounted() {
    console.log("Unmounted");
  },
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
