<template>
  <div class="hello">
    <svg
      version="1.1"
      id="Layer_1"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      x="0px"
      y="0px"
      width="800px"
      height="400px"
      viewBox="0 0 800 400"
      style="enable-background: new 0 0 800 400"
      xml:space="preserve"
    >
      >
      <rect id="background" class="st0" width="800" height="400" />
      <path
        id="square"
        class="st1"
        d="M525.667,321.333H274.333V78.667h251.333V321.333z"
      />
      <path
        id="star"
        class="st2"
        d="M400,82.531l38.168,77.336l85.346,12.401l-61.757,60.198l14.579,85.001L400,277.336l-76.336,40.132
  l14.579-85.001l-61.757-60.198l85.346-12.401L400,82.531z"
      />
    </svg>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { MorphSVGPlugin } from "gsap/MorphSVGPlugin";

gsap.registerPlugin(MorphSVGPlugin);
console.log("🚀 ~ file: HelloWorld.vue ~ line 38 ~ gsap", gsap)

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  mounted() {
    gsap.to("#square", {duration: 3, morphSVG:{shape:"#star", shapeIndex:5}});
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.st0 {
  fill: #1d1d1d;
  stroke: #000000;
  stroke-miterlimit: 10;
}
.st1 {
  fill: #88c540;
}
.st2 {
  fill: none;
  stroke: #e5285d;
  stroke-miterlimit: 10;
}
</style>
