<template>
  <div class="default-layout-wrapper">
    <NavigationBar ref="navigationBar" />
    <Nuxt />
    <BuyTickets />
    <Footer />
  </div>
</template>

<script>
import NavigationBar from "../components/NavigationBar.vue";
import Footer from "../components/Footer.vue";
import BuyTickets from "../components/BuyTickets.vue";
export default {
  props: {
    error: Object,
  },
  layout: "error",
  components: {
    NavigationBar,
    Footer,
    BuyTickets,
  },
  methods: {
    lockNavigationBar(event) {
      this.$refs.navigationBar.lockNavigation(event);
    },
  },
  mounted() {
    window.addEventListener("scroll", this.lockNavigationBar);
  },
};
</script>

<style>
</style>