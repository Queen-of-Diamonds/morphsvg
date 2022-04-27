<template>
  <div class="hello">
    <inline-svg :src="mySvg" @loaded="onLoaded"></inline-svg>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { MorphSVGPlugin } from "gsap/MorphSVGPlugin";
import InlineSvg from "vue-inline-svg";
import * as mySvg from "@/hippo.svg";

gsap.registerPlugin(MorphSVGPlugin);

export default {
  name: "Hippo",
  components: { InlineSvg },
  props: {
    msg: String,
  },
  data() {
    return {
      mySvg,
      svgHasLoaded: false,
    };
  },
  methods: {
    onLoaded() {
      this.svgHasLoaded = true;
      gsap.to("#elephant", {duration: 4, morphSVG:"#hippo"})
    },
  },
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
  fill: #cccccc;
}
</style>
