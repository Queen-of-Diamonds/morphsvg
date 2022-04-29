<template>
  <div class="alphabet">
    <alphabet-svg></alphabet-svg>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { MorphSVGPlugin } from "gsap/MorphSVGPlugin";
import AlphabetSvg from "@/alphabet.svg?inline";

gsap.registerPlugin(MorphSVGPlugin);

export default {
  name: "Alphabet",
  components: { AlphabetSvg },
  props: {
    msg: String,
  },
  data() {
    return {
      svgHasLoaded: false,
    };
  },
  mounted() {
    setTimeout(this.onLoaded, 2000);
  },
  methods: {
    onLoaded() {
      this.svgHasLoaded = true;

      MorphSVGPlugin.convertToPath("circle, #square, #triangle");

      var tl = gsap.timeline({
        repeat: 20,
        // repeatDelay: 0.3,
        yoyo: true,
        duration: 1,
        // defaults: { duration: 1 },
      });

      tl.to("#triangle", { morphSVG: "#a" })
        .to("#square", { morphSVG: "#b" })
        .to("#circle", { morphSVG: "#c" })
        .timeScale(3);
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
</style>
<style>
.st0 {
  fill: #1d1d1d;
}
.st1 {
  fill: #89c540;
}
.st2 {
  fill: #e24b6c;
}

#letters {
  visibility: hidden;
}
</style>
