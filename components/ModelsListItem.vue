<template>
  <div class="models-list-item-wrapper">
    <nuxt-link class="models-list-item-link" :to="'/models/' + modelItem.Id">
      <h3>{{ modelItem.modelName }}</h3>
      <h4>{{ modelItem.modelType }}</h4>
      <img :src="modelItem.modelPicture" alt="" />
    </nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    modelItem: Object,
  },
};
</script>

<style>
.models-list-item-wrapper {
  flex-basis: calc(20% - 12px);
}
.models-list-item-link {
  background: linear-gradient(#2d2d2d 0%, #505050 100%);
  border: 1px solid var(--primary-theme-color);
  text-decoration: none;
  display: inline-block;
  width: 100%;
  transition: transform 0.3s, box-shadow 0.3s;
  position: relative;
  height: 450px;
  box-sizing: border-box;
  padding: 2em;
}
.models-list-item-link:hover {
  transform: scale(1.02);
  box-shadow: 0 0 24px rgba(0, 0, 0, 0.16);
}
.models-list-item-link > h3 {
  margin: 0;
  color: var(--light-text-color);
  font-family: "Adobe Jenson Pro";
  font-size: 35px;
}
.models-list-item-link > h4 {
  margin: 3px 0 0;
  font-size: 16px;
  color: var(--light-text-color-dimmed);
  font-family: "Adobe Jenson Pro";
}
.models-list-item-link > img {
  position: absolute;
  bottom: 0;
  right: 0;
  object-fit: cover;
}
</style>