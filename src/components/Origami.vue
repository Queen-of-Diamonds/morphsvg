<template>
<div class="main-ctr">
  <div class="dialog-wrapper">
    <button class="open">Open Dialog</button>
    <button class="close">X</button>
    <p>Hello, it's me!<br>Mariooooo!</p>
    <origami-svg></origami-svg>
  </div>
</div>
</template>

<script>
import { gsap } from "gsap";
import { MorphSVGPlugin } from "gsap/MorphSVGPlugin";
import OrigamiSvg from "@/origami.svg?inline";

gsap.registerPlugin(MorphSVGPlugin);

export default {
  name: "Origami",
  components: { OrigamiSvg },
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

      // This design uses GSAP 2 https://codepen.io/balapa/pen/JYLMLr
      // I have made changes to some of the code using the GSAP 3 Migration Guide, GSAP 3 Release Notes and other articles.
      // GSAP 3 Migration Guide - https://greensock.com/3-migration/
      // GSAP 3 Release Notes - https://greensock.com/3-release-notes
      // Tips for Writing Animation Code Efficiently - https://css-tricks.com/tips-for-writing-animation-code-efficiently/

    gsap.set(close, {scale: 0, transformOrigin: "center center"});

 const tl = gsap.timeline();

open.on("click", function(){
  
  //Decided to comment this line out because it's giving an error
  // $(this).addClass("off");

tl.to("#box", {morphSVG:"#step1", delay: .3, ease: "power4", duration: .2})
  .to("#box", {morphSVG:"#step2", ease: "power4", duration: .2})
  .to("#box", {morphSVG:"#step3", ease: "power4", duration: .2})
  .to("#box", {morphSVG:"#step4", ease: "power4", duration: .2})
  .set("text", {className:"+=show"})
  
  .to(close, {scale: 1, delay: .3, ease: "bounce", duration: .3})
  });

close.on("click", function(){

  tl.to(close, {scale: 0, ease: "power4", duration: .3})
  .set("text", {className:"-=show"})
  .to("#box", {morphSVG:"#step3", delay: .3, ease: "power4", duration: .2})
  .to("#box", {morphSVG:"#step2", ease: "power4", duration: .2})
  .to("#box", {morphSVG:"#step1", ease: "power4", duration: .2})
  .to("#box", {morphSVG:"#step0", ease: "power4", duration: .2})
  
  .set(open, {className:"-=off"});
})
    }
  }
}

</script>

<style>
@import url(https://fonts.googleapis.com/css?family=Roboto:400,300);

body {
  display: table;
  width: 100%;
  height: 100%;
  background: -webkit-linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* Chrome 10+, Saf5.1+ */
  background:    -moz-linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* FF3.6+ */
  background:     -ms-linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* IE10 */
  background:      -o-linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* Opera 11.10+ */
  background:         linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* W3C */
  }

  button:focus {
  outline: none;
}

.main-ctr {
  display: table-cell;
  vertical-align: middle;
  text-align: center;
}

.dialog-wrapper {
  position: relative;
  display: inline-block;
  height: 249px;
  width: 369px;
}

p {
    position: absolute;
    top: 50%;
    margin-top: -24px;
    left: 0;
    right: 0;
    text-align: center;
    line-height: 1.5;
    font-family: "roboto";
    padding: 0 20px;
    box-sizing: border-box;
    font-weight: 300;
    opacity: 0;
    color: #999;
    transition: .45s all ease;
    pointer-events: none;
    letter-spacing: 1.5px;
}

.show {
      opacity: 1;
    }

    .open {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 160px;
    height: 45px;
    margin-top: -22.5px;
    margin-left: -80.5px;
    border: none;
    background: white;
    font-size: 14px;
    color: black;
    cursor: pointer;
    transition: .3s all ease;
    letter-spacing: 1.5px;
}

.off {
      pointer-events: none;
      opacity: 0;
    }

    .close {
    position: absolute;
    top: 25px;
    right: 25px;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: none;
    background: -webkit-linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* Chrome 10+, Saf5.1+ */
    background:    -moz-linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* FF3.6+ */
    background:     -ms-linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* IE10 */
    background:      -o-linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* Opera 11.10+ */
    background:         linear-gradient(90deg, #1CD8D2 10%, #93EDC7 90%); /* W3C */
    color: white;
    font-size: 16px;
    /* box-shadow: 0 1px 6px rgba(0,0,0,0.2); */
    cursor: pointer;
  }

</style>