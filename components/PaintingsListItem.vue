<template>
  <div class="paintings-list-item-wrapper">
    <img :src="painting.paintingImageSource" alt="" />
    <h3>{{ painting.paintingName }}</h3>
    <h4>{{ painting.paintingArtist }}</h4>
  </div>
</template>

<script>
export default {
  props: {
    painting: Object,
  },
};
</script>

<style>
.paintings-list-item-wrapper {
  font-family: "Adobe Jenson Pro";
  color: var(--light-text-color);
  transition: transform 0.3s;
  flex-basis: 100%;
  height: 60vh;
}
.paintings-list-item-wrapper:hover {
  transform: scale(1.02);
}
.paintings-list-item-wrapper > img {
  width: 100%;
  object-fit: cover;
  height: 100%;
  transition: box-shadow 0.3s;
  object-fit: cover;
}
.paintings-list-item-wrapper > img:hover {
  box-shadow: 0 0 24px rgba(0, 0, 0, 0.5);
}
.paintings-list-item-wrapper > h3 {
  font-size: 25px;
  margin: 0.72em 0 3px;
  font-weight: 400;
}
.paintings-list-item-wrapper > h4 {
  color: var(--light-text-color-dimmed);
  font-size: 16px;
  margin: 0;
  font-weight: 300;
}
</style>