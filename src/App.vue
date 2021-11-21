<template>
  <div id="app">
    <Header />
    <div id="content" class="content">
      <router-view />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from "@/components/layout/Header.vue";

export default {
  name: "App",
  components: {
    Header,
  },
};
</script>