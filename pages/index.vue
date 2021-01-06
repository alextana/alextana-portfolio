<template>
  <div class="canvas-container text-center">
    <Bubbles />
    <div class="title pre-anim intro">
      <div class="container mx-auto">
        <div class="main-content my-3">
          <h1 class="text-4xl intro pre-anim">Hi I'm Alex</h1>
          <h2 class="text-2xl intro pre-anim">
            Front end developer based in Brighton, UK.
          </h2>
        </div>
      </div>
      <NuxtLink to="/projects/"
        ><PrimaryButton class="intro">View my projects</PrimaryButton></NuxtLink
      >
    </div>
  </div>
</template>

<script>
import gsap from "gsap";
export default {
  mounted() {
    gsap.from(".intro", {
      opacity: 0,
      duration: ".5",
      autoAlpha: "0",
      y: "-200",
      delay: ".3",
      stagger: ".2",
    });
  },
};
</script>

<style>
body {
  background: #0d1317;
}
.pre-anim {
  visibility: hidden;
}
.menu .nuxt-link-exact-active {
  color: #27fb6b;
}
.punchline {
  font-style: italic;
}
.title {
  width: 90%;
  position: absolute;
  left: 50%;
  top: 50%;
  color: #fff;
  transform: translate(-50%, -50%);
}
.title h1 {
  line-height: 4rem;
  font-size: 4rem;
  font-weight: bold;
  font-family: "Nunito Sans";
  font-weight: "900";
  color: #27fb6b;
}
</style>
