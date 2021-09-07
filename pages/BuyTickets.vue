<template>
  <div class="buy-tickets-wrapper">
    <video src="/Never gonna give you up.mp4" controls autoplay="true"></video>
  </div>
</template>

<script>
export default {
  transition: "buy-tickets",
};
</script>

<style>
.buy-tickets-wrapper {
  margin-top: 8rem;
}
.buy-tickets-wrapper > video {
  display: block;
  width: fit-content;
  margin: 0 auto;
}
/* #region Transitions */
.buy-tickets-enter-active,
.buy-tickets-leave-active {
  transition: opacity 0.2s, transform 0.2s;
}
.buy-tickets-enter,
.buy-tickets-leave-active {
  opacity: 0;
  transform: scale(1.05);
}
/* #endregion */
</style>