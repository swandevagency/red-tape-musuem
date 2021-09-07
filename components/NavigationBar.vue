<template>
  <div class="navigation-bar-wrapper" ref="navigationBarWrapper">
    <h2 ref="websiteName">Red Tape</h2>
    <ul class="navigation-links-list" ref="navigationLinksList">
      <li><nuxt-link class="selected" to="Index">Home</nuxt-link></li>
      <li><nuxt-link to="Models">Models</nuxt-link></li>
      <li><nuxt-link to="Paintings">Paintings</nuxt-link></li>
      <li><nuxt-link to="#">GitHub</nuxt-link></li>
      <li><nuxt-link to="#">About</nuxt-link></li>
    </ul>
  </div>
</template>

<script>
import { gsap } from "gsap";
export default {
  computed: {
    isLockNavigation() {
      return this.$store.state.index.lockNavigation;
    },
  },
  methods: {
    lockNavigation(event) {
      if (window.scrollY != 0) {
        gsap.to(this.$refs.navigationBarWrapper, {
          backgroundColor: "#373737",
          boxShadow: "0 4px 6px 1px rgba(3,3,3,0.55)",
          duration: 0.3,
          ease: "power2.out",
        });
        gsap.to(this.$refs.navigationBarWrapper, {
          height:
            this.$refs.websiteName.offsetTop +
            (this.$refs.websiteName.offsetTop -
              this.$refs.websiteName.offsetTop / 2),
          duration: 0.3,
          ease: "power2.out",
        });
        gsap.to(this.$refs.navigationLinksList, {
          translateX:
            this.$refs.websiteName.offsetLeft +
            this.$refs.navigationLinksList.offsetLeft +
            34,
          translateY:
            this.$refs.websiteName.offsetTop -
            this.$refs.navigationLinksList.offsetTop,
          duration: 0.3,
          ease: "power2.out",
        });
      } else {
        gsap.to(this.$refs.navigationBarWrapper, {
          backgroundColor: "rgba(0,0,0,0)",
          boxShadow: "none",
          duration: 0.3,
          ease: "power2.out",
        });
        gsap.to(this.$refs.navigationBarWrapper, {
          height:
            this.$refs.websiteName.offsetTop +
            (this.$refs.websiteName.offsetTop +
              this.$refs.websiteName.offsetTop * 2),
          duration: 0.3,
          ease: "power2.out",
        });
        gsap.to(this.$refs.navigationLinksList, {
          translateX:
            this.$refs.websiteName.offsetLeft -
            this.$refs.navigationLinksList.offsetLeft,
          translateY:
            this.$refs.websiteName.offsetTop -
            this.$refs.navigationLinksList.offsetTop / 3.2,
          duration: 0.3,
          ease: "power2.out",
        });
      }
    },
  },
};
</script>

<style>
body {
  background-color: var(--background-color);
}
.navigation-bar-wrapper {
  overflow: hidden;
  display: flex;
  flex-direction: column;
  z-index: 4;
  top: 0;
  left: 0;
  width: 100%;
  padding: 0 80px 34px;
  position: fixed;
}
.navigation-bar-wrapper > h2 {
  font-size: 34px;
  font-family: "Perpetua Titling MT";
  font-weight: 300;
  margin: 1em 0;
  margin-right: 24px;
  color: var(--light-text-color);
}
.navigation-links-list {
  list-style: none;
  display: flex;
  padding: 0;
  margin: 0;
}
.navigation-links-list > li {
  margin: 0 24px 0 0;
  padding: 0;
  width: max-content;
}
.navigation-bar-wrapper li a {
  font-size: 15px;
  font-family: montserrat;
  font-weight: 300;
  text-decoration: none;
  color: var(--light-text-color);
  display: inline-block;
  padding: 0.5em 0;
}
.navigation-bar-wrapper li a.selected {
  font-weight: 500;
  border-bottom: 2px solid var(--primary-theme-color);
}
</style>