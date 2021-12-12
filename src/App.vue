<template>
  <v-app>
    <v-main>
      <Logo/>
      <Content/>
    </v-main>
  </v-app>
</template>

<script>
import Logo from "./components/Logo";
import Content from "./components/Content";

export default {
  name: "App",

  components: {
    Content,
    Logo,
  },

  data: () => ({
    //
  }),
};
</script>
