<template>
  <div class="about-page-wrapper">
    <div class="about-landing-wrapper">
      <div class="about-page-content-wrapper">
        <img src="/Red Tape museum logo.png" alt="" />
        <div class="about-page-description-wrapper">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Aliquam
            faucibus purus in massa tempor nec feugiat nisl. Ornare arcu odio ut
            sem. Consectetur adipiscing elit pellentesque habitant morbi
            tristique senectus. Eget nunc lobortis mattis aliquam faucibus purus
            in massa.
          </p>
          <nuxt-link class="section-link-button" to="BuyTickets"
            >BUY TICKETS</nuxt-link
          >
        </div>
      </div>
    </div>
    <section class="history-section">
      <div class="history-description-wrapper">
        <div class="history-section-image">
          <img src="/Landing image.jpg" alt="" />
        </div>
        <div class="history-content">
          <h2>History</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Aliquam
            faucibus purus in massa tempor nec feugiat nisl. Ornare arcu odio ut
            sem. Consectetur adipiscing elit pellentesque habitant morbi
            tristique senectus. Eget nunc lobortis mattis aliquam faucibus purus
            in massa. Labore et dolore magna aliqua. Aliquam faucibus purus in
            massa tempor nec feugiat nisl. Ornare arcu odio ut sem.
          </p>
        </div>
      </div>
    </section>
    <section class="our-experience-section">
      <div class="our-experience-description-wrapper">
        <div class="our-experience-content">
          <h2>Our experience</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Aliquam
            faucibus purus in massa tempor nec feugiat nisl. Ornare arcu odio ut
            sem. Consectetur adipiscing elit pellentesque habitant morbi
            tristique senectus. Eget nunc lobortis mattis aliquam faucibus purus
            in massa. Labore et dolore magna aliqua. Aliquam faucibus purus in
            massa tempor nec feugiat nisl. Ornare arcu odio ut sem.
          </p>
        </div>
        <div class="our-experience-section-image">
          <img src="/Our experience image.jpg" alt="" />
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  transition: "about",
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
.about-landing-wrapper {
  padding: 10em 80px 0;
  box-sizing: border-box;
  isolation: isolate;
  background: url("/About landing.jpg");
  background-size: cover;
  background-position: center;
  height: 100vh;
  overflow: hidden;
}
.about-page-content-wrapper {
  padding: 2em 0 6em;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.about-page-content-wrapper > img {
  width: 35%;
  margin: 0 auto;
}
.about-landing-wrapper::before {
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
.about-page-description-wrapper {
  padding-top: 2em;
  width: 40%;
  text-align: center;
  position: relative;
  color: var(--light-text-color);
}
.about-page-description-wrapper > p {
  font-family: montserrat;
  margin: 0;
  line-height: 30px;
  font-weight: 300;
}
.about-page-content-wrapper {
  width: 100%;
  margin: 2rem 0 0;
  display: flex;
  flex-direction: column;
}
.section-link-button {
  display: inline-block;
  margin-top: 2.1em;
  font-size: 20px;
  font-family: "Perpetua Titling MT";
  color: var(--light-text-color);
}
.about-page-description-wrapper::after {
  content: "";
  border: 3px solid var(--primary-theme-color);
  top: -8em;
  bottom: -2em;
  left: -2em;
  right: -2em;
  box-sizing: border-box;
  position: absolute;
  z-index: -1;
}
/* #region History section */
.history-section {
  padding: 13em 0 6em;
}
.history-description-wrapper {
  display: flex;
  padding: 0 80px;
  align-items: center;
  justify-content: center;
}
.history-section-image > img {
  aspect-ratio: 1 / 1;
  object-fit: cover;
  border: 3px solid var(--primary-theme-color);
  width: 100%;
}
.history-section-image {
  height: 100%;
  flex-basis: 35%;
}
.history-content {
  position: relative;
  margin-left: 34px;
  flex-basis: 50%;
  color: var(--light-text-color);
}
.history-content > h2 {
  font-size: 34px;
  margin: 0 0 0.5em;
  font-family: "Adobe Jenson Pro";
  font-weight: 300;
}
.history-content > p {
  font-family: montserrat;
  margin: 0;
  line-height: 30px;
  font-weight: 300;
}
.history-content::before {
  content: "";
  background-color: var(--background-color);
  top: -2em;
  bottom: -2em;
  left: -2em;
  right: 0em;
  box-sizing: border-box;
  position: absolute;
  z-index: -1;
}
.history-content::after {
  content: "";
  border: 3px solid var(--primary-theme-color);
  top: -4em;
  bottom: -4em;
  left: 2em;
  right: -2em;
  box-sizing: border-box;
  position: absolute;
  z-index: -2;
}
/* #endregion */
/* #region Our experience */
.our-experience-section {
  padding: 13em 0 6em;
}
.our-experience-description-wrapper {
  display: flex;
  padding: 0 80px;
  align-items: center;
  justify-content: center;
}
.our-experience-section-image > img {
  aspect-ratio: 1 / 1;
  object-fit: cover;
  border: 3px solid var(--primary-theme-color);
  width: 100%;
}
.our-experience-section-image {
  height: 100%;
  flex-basis: 35%;
}
.our-experience-content {
  position: relative;
  margin-right: 34px;
  flex-basis: 50%;
  color: var(--light-text-color);
}
.our-experience-content > h2 {
  font-size: 34px;
  margin: 0 0 0.5em;
  font-family: "Adobe Jenson Pro";
  font-weight: 300;
}
.our-experience-content > p {
  font-family: montserrat;
  margin: 0;
  line-height: 30px;
  font-weight: 300;
}
.our-experience-content::before {
  content: "";
  background-color: var(--background-color);
  top: -2em;
  bottom: -2em;
  left: 0em;
  right: -2em;
  box-sizing: border-box;
  position: absolute;
  z-index: -1;
}
.our-experience-content::after {
  content: "";
  border: 3px solid var(--primary-theme-color);
  top: -4em;
  bottom: -4em;
  left: -2em;
  right: 2em;
  box-sizing: border-box;
  position: absolute;
  z-index: -2;
}
/* #endregion */
/* #region Transitions */
.about-enter-active,
.about-leave-active {
  transition: opacity 0.2s, transform 0.2s;
}
.about-enter,
.about-leave-active {
  opacity: 0;
  transform: scale(1.05);
}
/* #endregion */
</style>