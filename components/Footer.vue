<template>
  <div class="footer-wrapper">
    <div class="footer-title-wrapper">
      <h2>RED TAPE</h2>
      <h6>ITALIAN ART MUSEUM</h6>
    </div>
    <div class="footer-content-wrapper">
      <div class="footer-navigation-links-wrapper">
        <h2>Navigate</h2>
        <ul class="footer-navigation-links-list">
          <li><nuxt-link to="/">Home</nuxt-link></li>
          <li><nuxt-link to="/models">Models</nuxt-link></li>
          <li><nuxt-link to="/paintings">Paintings</nuxt-link></li>
          <li>
            <a href="https://github.com/swandevagency" target="_blank"
              >GitHub</a
            >
          </li>
          <li><nuxt-link to="/about">About</nuxt-link></li>
        </ul>
      </div>
      <div class="footer-descriptions-wrapper">
        <div class="footer-address-wrapper">
          <h2>Address</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt
          </p>
        </div>
        <div class="footer-social-media-links-wrapper">
          <h2>Social media</h2>
          <ul class="footer-social-media-links-list">
            <li>
              <a href=""
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                >
                  <path
                    id="Instagram_icon"
                    data-name="Instagram icon"
                    d="M10,3a7.008,7.008,0,0,0-7,7V20a7.008,7.008,0,0,0,7,7H20a7.008,7.008,0,0,0,7-7V10a7.008,7.008,0,0,0-7-7ZM22,7a1,1,0,1,1-1,1A1,1,0,0,1,22,7ZM15,9a6,6,0,1,1-6,6A6.006,6.006,0,0,1,15,9Zm0,2a4,4,0,1,0,4,4,4,4,0,0,0-4-4Z"
                    transform="translate(-3 -3)"
                    fill="#f5f5f5"
                  />
                </svg>
              </a>
            </li>
            <li>
              <a href="">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                >
                  <path
                    id="Linkedin_icon"
                    data-name="Linkedin icon"
                    d="M25.818,4H6.182A2.181,2.181,0,0,0,4,6.182V25.818A2.181,2.181,0,0,0,6.182,28H25.818A2.181,2.181,0,0,0,28,25.818V6.182A2.181,2.181,0,0,0,25.818,4ZM11.586,23.636H8.368V13.281h3.218ZM9.944,11.8A1.876,1.876,0,1,1,11.82,9.925,1.876,1.876,0,0,1,9.944,11.8Zm13.7,11.835H20.425V18.6c0-1.2-.022-2.746-1.672-2.746-1.675,0-1.932,1.308-1.932,2.659v5.123H13.6V13.281h3.087V14.7h.044a3.382,3.382,0,0,1,3.045-1.672c3.259,0,3.861,2.145,3.861,4.933v5.679Z"
                    transform="translate(-4 -4)"
                    fill="#f5f5f5"
                  />
                </svg>
              </a>
            </li>
            <li>
              <a href="https://github.com/swandevagency" target="_blank">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="24.376"
                  height="24"
                  viewBox="0 0 24.376 24"
                >
                  <path
                    id="Github_icon"
                    data-name="Github icon"
                    d="M15.188,3a12.181,12.181,0,0,0-2.954,24,1.779,1.779,0,0,1-.093-.592V24.325H10.609A2.121,2.121,0,0,1,8.674,23.3c-.4-.74-.468-1.873-1.457-2.566-.294-.231-.07-.494.268-.458a3.194,3.194,0,0,1,1.63,1.241,1.566,1.566,0,0,0,1.621.781,11.645,11.645,0,0,0,1.717-.123,3.823,3.823,0,0,1,1.613-1.993c-4.059-.417-6-2.437-6-5.178a4.981,4.981,0,0,1,1.357-3.284c-.28-.955-.633-2.9.108-3.643a4.242,4.242,0,0,1,3.2,1.5,9.216,9.216,0,0,1,5.927,0,4.24,4.24,0,0,1,3.2-1.506c.743.742.387,2.7.1,3.65a4.98,4.98,0,0,1,1.349,3.277c0,2.739-1.934,4.757-5.986,5.177a4.275,4.275,0,0,1,1.929,3.449v2.777a1.787,1.787,0,0,1-.036.272A12.181,12.181,0,0,0,15.188,3Z"
                    transform="translate(-3 -3)"
                    fill="#f5f5f5"
                  />
                </svg>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.footer-wrapper {
  padding: 2.5em 130px;
  border-top: 1px solid var(--secondary-theme-color);
  background-color: var(--footer-background-color);
  color: var(--light-text-color);
}
.footer-content-wrapper h2 {
  font-family: "Adobe Jenson Pro";
}
.footer-title-wrapper {
  text-align: center;
}
.footer-title-wrapper > h2 {
  margin: 0;
  font-family: "Perpetua Titling MT";
  font-weight: 300;
}
.footer-title-wrapper > h6 {
  margin: 3px 0 0;
  color: var(--light-text-color-dimmed);
}
.footer-content-wrapper {
  margin-top: 40px;
  display: flex;
  justify-content: center;
}
.footer-navigation-links-wrapper {
  flex-basis: calc(50% - 12px);
}
.footer-descriptions-wrapper {
  flex-basis: calc(50% - 12px);
}
.footer-address-wrapper > p {
  font-family: montserrat;
  font-size: 15px;
}
.footer-navigation-links-list {
  display: flex;
  margin: 0;
  padding: 0;
  flex-direction: column;
  flex-basis: calc(20% - 24px);
  list-style: none;
}
.footer-navigation-links-list > li {
  margin: 0 0 18px;
}
.footer-navigation-links-list > li > a {
  color: var(--light-text-color);
  font-family: montserrat;
  font-weight: 300;
  text-decoration: none;
}
.footer-social-media-links-wrapper {
  margin-top: 40px;
}
.footer-navigation-links-list > li > a.nuxt-link-exact-active {
  border-left: 2px solid var(--primary-theme-color);
  padding-left: 8px;
  margin-left: -8px;
  font-weight: 500;
}
.footer-social-media-links-list {
  list-style-type: none;
  display: flex;
  padding: 0;
}
.footer-social-media-links-list > li {
  margin-right: 18px;
}
</style>