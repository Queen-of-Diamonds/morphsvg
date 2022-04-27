<template>
  <div class="hello">
    <inline-svg :src="mySvg" @loaded="onLoaded"></inline-svg>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { MorphSVGPlugin } from "gsap/MorphSVGPlugin";
import InlineSvg from "vue-inline-svg";
import * as mySvg from "@/star.svg";

gsap.registerPlugin(MorphSVGPlugin);
console.log("🚀 ~ file: HelloWorld.vue ~ line 38 ~ gsap", gsap);

export default {
  name: "HelloWorld",
  components: { InlineSvg },
  props: {
    msg: String,
  },
  data() {
    return {
      mySvg,
      svgHasLoaded: false
    };
  },
  methods: {
    onLoaded() {
      this.svgHasLoaded = true;
      gsap.to("#square", {
        duration: 3,
        morphSVG: { shape: "#star", shapeIndex: 5 },
      });
    }
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
