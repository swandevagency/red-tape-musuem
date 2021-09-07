<template>
  <div class="model-viewer-page-wrapper">
    <h2>Models</h2>
    <div class="model-viewer-wrapper">
      <div class="model-viewer-visualization-wrapper">
        <canvas
          class="model-viewer-visualization-render-canvas"
          ref="modelViewerRenderCanvas"
        ></canvas>
      </div>
      <div class="model-viewer-information-wrapper">
        <h2>
          {{ $store.state.models.modelsList[$route.params.Id].modelName }}
        </h2>
        <h3>
          {{ $store.state.models.modelsList[$route.params.Id].modelType }}
        </h3>
        <p>
          {{
            $store.state.models.modelsList[$route.params.Id].modelDescription
          }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import * as THREE from "three";
import { gsap } from "gsap";
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls.js";
import { GLTFLoader } from "three/examples/jsm/loaders/GLTFLoader.js";
export default {
  transition: "model",
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
      -0.75,
      0.75,
      0.75,
      -0.75,
      0.1,
      10
    );
    this.camera.position.z = 1;
    this.controls = new OrbitControls(
      this.camera,
      this.$refs.modelViewerRenderCanvas
    );
    this.controls.enableDamping = true;
    // this.controls.enabled = false;
    // Adding to the scene
    this.scene.add(this.camera);
    this.scene.add(directionalLight);
    this.scene.add(pointLightCreamy);
    this.scene.add(ambientLight);
    const targetModel = new GLTFLoader().load(
      `/Models/${
        this.$store.state.models.modelsList[this.$route.params.Id].modelPath
      }/${
        this.$store.state.models.modelsList[this.$route.params.Id].modelPath
      }_01_2k.gltf`,
      (gltf) => {
        gltf.scene.children.forEach((element) => {
          element.position.y = -0.32;
          element.castShadow = true;
          element.rotation.y = Math.PI / 5;
          this.scene.add(element);
        });
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
      canvas: this.$refs.modelViewerRenderCanvas,
      alpha: true,
    });
    this.renderer.setClearColor(0x000000, 0);
    this.renderer.setSize(
      this.$refs.modelViewerRenderCanvas.clientWidth,
      this.$refs.modelViewerRenderCanvas.clientHeight
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
.model-viewer-page-wrapper {
  padding: 10em 80px 0;
  margin: 2rem 0 0;
}
.model-viewer-page-wrapper > h2 {
  text-align: center;
  font-size: 34px;
  padding: 0.5em 0;
  border-bottom: 1px solid var(--secondary-theme-color);
  margin: 0 0 0.5em;
  color: var(--light-text-color);
  font-family: "Adobe Jenson Pro";
  font-weight: 300;
}
.model-viewer-wrapper {
  display: flex;
  align-items: center;
  margin-top: 8rem;
  justify-content: center;
}
.model-viewer-visualization-wrapper {
  height: 32em;
  flex-basis: 35%;
}
.model-viewer-information-wrapper {
  margin-left: 34px;
  flex-basis: 35%;
}
.model-viewer-visualization-render-canvas {
  aspect-ratio: 1 / 1;
  mask-image: radial-gradient(
    circle,
    rgba(255, 255, 255, 1) 50%,
    rgba(255, 255, 255, 0) 70%
  );
  width: 100%;
}
.model-viewer-information-wrapper {
  position: relative;
  color: var(--light-text-color);
}
.model-viewer-information-wrapper::before {
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
.model-viewer-information-wrapper::after {
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
.model-viewer-information-wrapper > h2 {
  font-size: 34px;
  margin: 0;
  font-family: "Adobe Jenson Pro";
  font-weight: 300;
}
.model-viewer-information-wrapper > h3 {
  margin: 3px 0 1.2em;
  font-size: 16px;
  color: var(--light-text-color-dimmed);
  font-family: "Adobe Jenson Pro";
}
.model-viewer-information-wrapper > p {
  font-family: montserrat;
  margin: 0;
  line-height: 30px;
  font-weight: 300;
}
/* #region Transitions */
.model-enter-active,
.model-leave-active {
  transition: opacity 0.2s, transform 0.2s;
}
.model-enter,
.model-leave-active {
  opacity: 0;
  transform: scale(1.05);
}
/* #endregion */
</style>