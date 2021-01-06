<template>
  <nav class="navigation absolute">
    <div
      class="container mx-auto text-center md:text-left grid md:grid-cols-2 m-3"
    >
      <NuxtLink to="/">
        <div class="logo self-center">
          <span class="logo-letter">a</span>
          <span class="logo-letter">l</span>
          <span class="logo-letter">e</span>
          <span class="logo-letter">x</span>
          <span class="logo-letter logo-letter-last">t</span>
          <span class="logo-letter logo-letter-last">a</span>
          <span class="logo-letter logo-letter-last">n</span>
          <span class="logo-letter logo-letter-last">a</span>
        </div>
      </NuxtLink>
      <ul class="menu my-4 text-center md:text-right self-center">
        <NuxtLink to="/projects/"
          ><li class="inline mr-8">Projects</li></NuxtLink
        >
        <NuxtLink to="/about/"><li class="inline">About</li></NuxtLink>
      </ul>
    </div>
  </nav>
</template>

<script>
import gsap from "gsap";
export default {
  methods: {
    logoAnim() {
      gsap.from(".logo-letter", {
        opacity: 0,
        duration: ".5",
        autoAlpha: "0",
        x: "-200",
        stagger: ".2",
      });
    },
  },
  mounted() {
    this.logoAnim();
  },
};
</script>

<style>
nav {
  width: 100%;
  top: 0;
  left: 0;
}

.menu {
  color: white;
  font-size: 1.3rem;
  font-weight: 900;
}
.menu li {
  position: relative;
  padding-bottom: 10px;
  transition: 0.2s ease;
}
.menu li:hover {
  color: #27fb6b;
}
.logo {
  width: auto;
  font-size: 2.4rem;
  letter-spacing: -6px;
  color: white;
  transition: 0.2s ease;
  font-weight: 900;
}
.logo:hover {
  color: #27fb6b;
}
.logo-letter {
  display: inline-block;
  visibility: hidden;
}
.logo-letter-last {
  font-weight: normal;
  margin: 0;
  padding: 0;
}
nav {
  z-index: 999;
}
</style>