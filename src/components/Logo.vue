<template>
  <div>
    <img src="../assets/fartexcup.png" :class="{'mobile-image-size' : isMobile}"/>
  </div>
</template>

<script>
export default {
  name: "Logo.vue",
  computed: {
    isMobile() {
      return this.$vuetify.breakpoint.smAndDown;
    }
  }
};
</script>

<style scoped lang="scss">
div {
  margin: 50px 0 25px;
  text-align: center;

  img {
    max-width: 400px;
  }
  .mobile-image-size {
    width: 90%;
  }
}
</style>
