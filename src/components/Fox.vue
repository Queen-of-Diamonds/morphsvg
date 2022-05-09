<template>
  <div class="fox">
    <inline-svg :src="mySvg" @loaded="onLoaded"></inline-svg>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { MorphSVGPlugin } from "gsap/MorphSVGPlugin";
import InlineSvg from "vue-inline-svg";
import * as mySvg from "@/fox.svg";

gsap.registerPlugin(MorphSVGPlugin);
gsap.config({ nullTargetWarn: false });

export default {
  name: "Fox",
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
  mounted() {
    setTimeout(this.onLoaded, 2000);
  },
  methods: {
    onLoaded() {
      this.svgHasLoaded = true;

      MorphSVGPlugin.convertToPath("polygon, polyline");

        const tl = gsap.timeline({
          repeat:-1,
          delay:2,
          repeatDelay:2,
          yoyo: true,
      	});
        

      tl.to("legLeft", .1, {morphSVG:"#metalLegLeft", ease: "Power2", y: 0, }, .5)
        .to("legRight", .1, {morphSVG:"#metalLegRight", ease: "Power2", y: 0 }, .5)
        .to("handRight", .4, {morphSVG:"#metalRightHand", ease: "Back", y: 0 }, .5)
        .to("handLeft", .4, {morphSVG:"#metalLeftHand", ease: "Back", y: 0 }, .5)
        .to("armLeft", .4, {morphSVG:"#metalLeftArm", ease: "Back", y: 0 }, .5)
        .to("armRight", .4, {morphSVG:"#metalRightArm", ease: "Back", y: 0 }, .5)
        .to("blackNose", .4, {morphSVG:"#metalNose", ease: "Bounce", y: 0 }, .5)
        .to("eyeSpotLeft", .4, {morphSVG:"#metalEyeDotLeft", ease:"Back", y: 0 }, .3)
        .to("eyeSpotRight", .4, {morphSVG:"#metalEyeDotRight", ease: "Back", y: 0 }, .3)
        .to("eyeLeft", .4, {morphSVG:"#metalLeftEyeBlack", ease: "Bounce", y: 0 }, .3)
        .to("eyeRight", .4, {morphSVG:"#metalRightEyeBlack", ease: "Bounce", y: 0 }, .3)
        .to("eyeLeftWhite", .4, {morphSVG:"#metalLeftEyeWhite", fill:"#ffffff", ease: "Back", y: 0 }, .5)
        .to("eyeRightWhite", .4, {morphSVG:"#metalRightEyeWhite", fill:"#ffffff", ease: "Back", y: 0 }, .5)
        .to("mouth", .4, {morphSVG:"#metalMouth", fill:"#D0021B", stroke:"#000", strokeWidth: 4, ease: "Bounce", y: 0 }, .5)
        .to("teeth", .4, {morphSVG:"#metalTeeth", fill:"#fff", stroke:"#000", strokeWidth: 2, ease: "Bounce", y: 0 }, .5)
        .to("rage", .5, { opacity:1, ease: "Power2"}, .5);
    },
  },
};

</script>

<style>
body {
  background: #cde7f0;
}

svg {
  margin: 50px auto;
  display: block;
  max-width: 100%;
}

#metalLeftEyeWhite,
#metalRightEyeWhite,
#rage {
  opacity: 0;
}

#metalNose,
#metalLeftEyeBlack,
#metalRightEyeBlack,
#metalEyeDotLeft,
#metalEyeDotRight,
#metalLeftArm,
#metalLeftHand,
#metalRightArm,
#metalRightHand,
#metalLegLeft,
#metalLegRight,
#metalMouth,
#metalTeeth {
  display: none;
}
</style>
