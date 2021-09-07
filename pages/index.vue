<template>
  <div class="nuxt-app-wrapper">
    <div class="landing-page-wrapper">
      <div class="paintings-content-wrapper">
        <h2>Paintings</h2>
        <div class="paintings-list-wrapper">
          <PaintingsListItem
            v-for="painting in paintingsList"
            :key="painting.Id"
            :painting="painting"
          />
        </div>
      </div>
    </div>
    <section class="about-section">
      <div
        class="about-description-wrapper"
        @mousemove="interactWithStatue"
        ref="aboutContent"
      >
        <div class="about-section-statue-image">
          <canvas
            ref="statueRenderCanvas"
            class="about-section-statue-render-canvas"
          ></canvas>
        </div>
        <div class="about-content">
          <h2>About</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua. Aliquam
            faucibus purus in massa tempor nec feugiat nisl. Ornare arcu odio ut
            sem. Consectetur adipiscing elit pellentesque habitant morbi
            tristique senectus. Eget nunc lobortis mattis aliquam faucibus purus
            in massa.
          </p>
          <nuxt-link class="section-link-button" to="None">READ MORE</nuxt-link>
        </div>
      </div>
    </section>
    <section class="models-content-wrapper">
      <h2>Models</h2>
      <div class="models-list-wrapper">
        <ModelsListItem
          v-for="modelItem in modelsList"
          :key="modelItem.Id"
          :modelItem="modelItem"
        />
      </div>
    </section>
  </div>
</template>

<script>
import NavigationBar from "../components/NavigationBar.vue";
import * as THREE from "three";
import PaintingsListItem from "../components/PaintingsListItem.vue";
import { gsap } from "gsap";
import ModelsListItem from "../components/ModelsListItem.vue";
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls.js";
import { GLTFLoader } from "three/examples/jsm/loaders/GLTFLoader.js";
// import { mapMutations } from "vuex";
export default {
  computed: {
    paintingsList() {
      return this.$store.state.paintings.paintingItemsList;
    },
    modelsList() {
      return this.$store.state.models.modelsList;
    },
  },
  components: {
    NavigationBar,
    PaintingsListItem,
    ModelsListItem,
  },
  data() {
    return {
      camera: Object,
      scene: Object,
      renderer: Object,
      controls: Object,
    };
  },
  methods: {
    // Updating renderer every single frame
    tick() {
      this.controls.update();
      this.renderer.render(this.scene, this.camera);
      window.requestAnimationFrame(this.tick);
    },
    interactWithStatue(event) {
      const cursor = {
        positionX:
          ((event.pageX - this.$refs.aboutContent.offsetLeft) /
            this.$refs.aboutContent.clientWidth -
            0.5) *
          0.35,
        positionY:
          -(
            (event.pageY - this.$refs.aboutContent.offsetTop) /
              this.$refs.aboutContent.clientHeight -
            0.5
          ) * 0.35,
      };
      gsap.to(this.camera.position, {
        x: -cursor.positionX,
        y: -cursor.positionY,
        duration: 2,
        ease: "power3.out",
      });
    },
  },
  mounted() {
    // Defining object variables
    this.scene = new THREE.Scene();
    const directionalLight = new THREE.DirectionalLight("white", 1);
    const ambientLight = new THREE.AmbientLight("white", 1);
    const pointLightCreamy = new THREE.PointLight("#c4a280", 1);
    directionalLight.position.set(1, 1, 5);
    directionalLight.castShadow = true;
    directionalLight.shadow.mapSize.set(1024, 1024);
    directionalLight.shadow.camera.far = 15;
    directionalLight.shadow.camera.left = -7;
    directionalLight.shadow.camera.top = 7;
    directionalLight.shadow.camera.right = 7;
    directionalLight.shadow.camera.bottom = -7;
    pointLightCreamy.position.set(-1, -1, -3);
    this.camera = new THREE.OrthographicCamera(
      -0.25,
      0.25,
      0.25,
      -0.25,
      0.1,
      10
    );
    this.camera.position.z = 0.5;
    this.controls = new OrbitControls(
      this.camera,
      this.$refs.statueRenderCanvas
    );
    this.controls.enableDamping = true;
    this.controls.enabled = false;
    // Adding to the scene
    this.scene.add(this.camera);
    this.scene.add(directionalLight);
    this.scene.add(pointLightCreamy);
    this.scene.add(ambientLight);
    const statueModel = new GLTFLoader().load(
      "/Models/Statue model/marble_bust_01_2k.gltf",
      (gltf) => {
        gltf.scene.children[0].position.y = -0.32;
        gltf.scene.children[0].castShadow = true;
        gltf.scene.children[0].rotation.y = Math.PI / 5;
        this.scene.add(gltf.scene.children[0]);
      },
      (progress) => {
        console.log(progress);
      },
      (error) => {
        console.log(error);
      }
    );
    // Defining renderer
    this.renderer = new THREE.WebGLRenderer({
      canvas: this.$refs.statueRenderCanvas,
      alpha: true,
    });
    this.renderer.setClearColor(0x000000, 0);
    this.renderer.setSize(
      this.$refs.statueRenderCanvas.clientWidth,
      this.$refs.statueRenderCanvas.clientHeight
    );
    this.tick();
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
.landing-page-wrapper {
  padding: 10em 80px 0;
  box-sizing: border-box;
  isolation: isolate;
  background: url("/Landing image.jpg");
  background-size: cover;
  background-position: center;
  height: 100vh;
  overflow: hidden;
}
.landing-page-wrapper::before {
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
.paintings-content-wrapper {
  width: 100%;
  margin: 2rem 0 0;
  display: flex;
  flex-direction: column;
}
.paintings-content-wrapper > h2 {
  font-family: montserrat;
  color: var(--light-text-color);
  font-weight: 300;
}
.paintings-list-wrapper {
  display: flex;
}
/* #region About section */
.about-section {
  padding: 13em 0 6em;
}
.about-description-wrapper {
  display: flex;
  padding: 0 80px;
  align-items: center;
  justify-content: center;
}
.about-section-statue-render-canvas {
  aspect-ratio: 1 / 1;
  mask-image: radial-gradient(
    circle,
    rgba(255, 255, 255, 1) 20%,
    rgba(255, 255, 255, 0) 70%
  );
  width: 100%;
}
.about-section-statue-image {
  height: 32em;
  flex-basis: 35%;
}
.about-content {
  position: relative;
  margin-left: 34px;
  flex-basis: 50%;
  color: var(--light-text-color);
}
.about-content > h2 {
  font-size: 34px;
  margin: 0 0 0.5em;
  font-family: "Adobe Jenson Pro";
  font-weight: 300;
}
.about-content > p {
  font-family: montserrat;
  margin: 0;
  line-height: 30px;
  font-weight: 300;
}
.section-link-button {
  display: inline-block;
  margin-top: 2.1em;
  font-size: 20px;
  font-family: "Perpetua Titling MT";
  color: var(--light-text-color);
}
.about-content::before {
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
.about-content::after {
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
/* #region Models section */
.models-content-wrapper {
  box-sizing: border-box;
  padding: 6em 80px;
  width: 100%;
  margin: 1rem 0 0;
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
  justify-content: space-between;
}
/* #endregion */
</style>