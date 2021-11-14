<template>
  <div>
    <section
      class="container grid justify-center lg:justify-start lg:gap-8 lg:grid-flow-col lg:auto-cols-max text-center lg:text-left mx-auto my-8"
    >
      <div class="image-content self-center">
        <img
          class="rounded-full profile-img pre-anim"
          src="~/assets/img/profile.jpg"
        />
      </div>
      <div class="info-content self-center">
        <div class="section-info my-8 py-8">
          <h1 class="about about-heading pre-anim">Who is this guy?</h1>
          <p class="my-4 about about-sub pre-anim">
            "pineapple does go on pizza"
          </p>
          <p class="about about-text pre-anim">
            I'm a front end developer based in Brighton UK, originally from San
            Mauro Pascoli IT.
          </p>
          <p class="about pre-anim">
            Currently working at
            <a href="https://barkweb.co.uk" target="_blank" noopener noreferrer
              >Barkweb</a
            >
            building
            <a href="https://jolojo.com" target="_blank" noopener noreferrer
              >Jolojo CMS</a
            >.
          </p>
          <div class="skills pre-anim">
            <h3 class="about-head my-3">Wanna work with me?</h3>
            <a href="mailto:alex.tana1992@gmail.com"
              ><PrimaryButton>@ Drop me a line!</PrimaryButton></a
            >
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import gsap from "gsap";
export default {
  transition: "slideUp",
  mounted() {
    gsap.from(".profile-img", {
      opacity: 0,
      autoAlpha: 0,
      delay: "1.5"
    });
    gsap.from(".skills", {
      opacity: 0,
      autoAlpha: "0",
      delay: ".9",
      y: "200"
    });
    gsap.from(".about", {
      opacity: 0,
      duration: ".5",
      autoAlpha: "0",
      y: "-200",
      delay: ".5",
      stagger: ".2"
    });
  }
};
</script>

<style>
.about-heading {
  color: #27fb6b;
}
.about-head {
  font-size: 2.3rem;
}
.about-sub {
  font-style: italic;
  font-size: 1.3rem;
}
.slideUp-enter-active,
.slideUp-leave-active {
  transition: 0.4s ease;
}
.slideUp-enter,
.slideUp-leave-active {
  transform: translate(0%, 100%);
}
</style>
