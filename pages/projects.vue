<template>
  <div>
    <section class="container mx-auto my-8">
      <div class="section-info text-center my-8 py-8">
        <h1 class="project about-heading">My projects</h1>
        <p class="my-4 project">
          Here is a small collection of personal and professional projects I've
          completed over the years.
        </p>
      </div>
      <Projects />
    </section>
  </div>
</template>

<script>
import gsap from "gsap";

export default {
  layout: "default",
  transition: "slide",
  methods: {},
  mounted() {
    gsap.from(".card", {
      opacity: 0,
      duration: ".5",
      autoAlpha: "0",
      y: "200",
      delay: ".5",
      stagger: ".2"
    });
    gsap.from(".project", {
      opacity: 0,
      duration: ".3",
      autoAlpha: "0",
      y: "200",
      delay: ".6",
      stagger: ".1"
    });
  },
  destroyed() {
    gsap.to(".card", {
      opacity: 0,
      duration: ".2",
      opacity: "0",

      delay: "0",
      stagger: "0"
    });
  }
};
</script>

<style>
body {
  color: white;
}
.menu .nuxt-link-exact-active {
  color: #27fb6b;
}
.slide-enter-active,
.slide-leave-active {
  transition: 0.4s ease;
}

.slide-enter,
.slide-leave-active {
  transform: translate(-100%, 0);
}
</style>
