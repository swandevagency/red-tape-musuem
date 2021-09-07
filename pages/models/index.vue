<template>
  <div class="models-page-wrapper">
    <div class="landing-wrapper">
      <div class="models-content-wrapper">
        <h2>Models</h2>
        <div class="models-list-wrapper">
          <ModelsListItem
            v-for="modelItem in modelsList"
            :key="modelItem.Id"
            :modelItem="modelItem"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ModelsListItem from "../../components/ModelsListItem.vue";
export default {
  transition: "models",
  computed: {
    modelsList() {
      return this.$store.state.models.modelsList;
    },
  },
  components: {
    ModelsListItem,
  },
};
</script>

<style>
:root {
  --light-text-color: #f5f5f5;
  --light-text-color-dimmed: #878787;
  --background-color: #232323;
  --footer-background-color: #373737;
  --primary-theme-color: #ba3b3a;
  --secondary-theme-color: #c4a280;
}
::selection {
  color: var(--light-text-color);
  background-color: var(--primary-theme-color);
}
::-webkit-scrollbar {
  width: 12px;
}
::-webkit-scrollbar-track {
  background-color: #575757;
}
::-webkit-scrollbar-track:hover {
  background-color: #656565;
}
::-webkit-scrollbar-thumb {
  background-color: #434343;
  border-radius: 10px;
}
::-webkit-scrollbar-thumb:hover {
  background-color: #494949;
}
body {
  padding: 0;
  margin: 0;
}
.landing-wrapper {
  padding: 10em 80px 0;
  box-sizing: border-box;
  isolation: isolate;
  background: url("/Models landing image.jpg");
  background-size: cover;
  background-position: center;
  height: 100vh;
  overflow: hidden;
}
.landing-wrapper::before {
  content: "";
  background: linear-gradient(
    rgba(0, 0, 0, 0.6) 0%,
    rgba(30, 30, 30, 0.8) 100%
  );
  width: 100%;
  height: 100%;
  inset: 0;
  position: absolute;
  z-index: -1;
}
.models-content-wrapper {
  width: 100%;
  margin: 2rem 0 0;
  display: flex;
  flex-direction: column;
}
.models-content-wrapper > h2 {
  font-family: montserrat;
  color: var(--light-text-color);
  font-weight: 300;
}
.models-list-wrapper {
  display: flex;
}
/* #endregion */
/* #region Transitions */
.models-enter-active,
.models-leave-active {
  transition: opacity 0.2s, transform 0.2s;
}
.models-enter,
.models-leave-active {
  opacity: 0;
  transform: scale(1.05);
}
/* #endregion */
</style>