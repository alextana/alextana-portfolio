<template>
  <div class="my-6 grid md:grid-cols-3 gap-5">
    <div
      class="card text-white pre-anim rounded-2xl overflow-hidden"
      v-for="project in projects"
      :key="project.name"
    >
      <img class="w-full" :src="require(`~/assets/img/${project.image}.png`)" />
      <div class="card-content p-4">
        <h3 class="text-2xl font-bold">{{ project.name }}</h3>
        <p class="desc">{{ project.desc }}</p>
        <div class="tech-used text-gray-600 my-4">
          <p v-if="project.techUsed !== ''" class="font-bold">Tech used:</p>
          {{ project.techUsed }}
        </div>
        <div class="project-links grid grid-flow-col gap-3">
          <a
            v-if="project.siteLink !== ''"
            :href="project.siteLink"
            target="_blank"
            noopener
            noreferrer
            ><PrimaryButton class="w-full">View Site</PrimaryButton></a
          >
          <a
            class="w-full"
            v-if="project.githubLink !== ''"
            :href="project.githubLink"
            target="_blank"
            noopener
            noreferrer
            ><PrimaryButton class="w-full">Github</PrimaryButton></a
          >

          <a
            class="w-full"
            v-if="project.codepenLink !== ''"
            :href="project.codepenLink"
            target="_blank"
            noopener
            noreferrer
            ><PrimaryButton class="w-full">Codepen</PrimaryButton></a
          >

          <a
            class="w-full"
            v-if="project.adobeXDLink !== ''"
            :href="project.adobeXDLink"
            target="_blank"
            noopener
            noreferrer
            ><PrimaryButton class="w-full">Adobe XD</PrimaryButton></a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      projects: [
        {
          name: "Electric Calculator",
          image: "electric-calculator",
          desc:
            "Plug and play solution to calculate whether an electric vehicle is suitable for the client's needs based on user input",
          siteLink:
            "https://www.heritageautomotive.co.uk/electric-calculator/dist/index.html",
          techUsed: "Vue, Webpack, Bootstrap 4, Vue Formulate, Vue Form Wizard",
          githubLink: "",
          adobeXDLink: "",
          codepenLink: ""
        },
        {
          name: "blobs.js",
          image: "blobs",
          desc:
            "Plugin that generates particles with built-in controls to play with",
          githubLink: "https://github.com/alextana/blobs",
          siteLink: "https://blobsjs.netlify.com/",
          techUsed: "Vanilla JS, HTML, CSS",
          adobeXDLink: "",
          codepenLink: ""
        },
        {
          name: "Give me colors",
          image: "givemecolors",
          desc:
            "Plugin that outputs a wide selection of colours based on the selected shade",
          githubLink: "https://github.com/alextana/givemeacolor",
          siteLink: "https://givemecolors.netlify.com/",
          techUsed: "Vanilla JS, HTML, CSS",
          adobeXDLink: "",
          codepenLink: ""
        },
        {
          name: "Auto100",
          image: "auto100",
          desc: "Professional project for Auto100, luxury car dealership",
          techUsed: "HTML, CSS, Javascript, GSAP",
          githubLink: "",
          siteLink: "http://aut58495.dev.cogplatform.co.uk/",
          adobeXDLink: "",
          codepenLink: ""
        },
        {
          name: "Hartwell Group",
          image: "hartwell",
          desc:
            "Professional project for Hartwell Group, first one to integrate Vue JS with Bluesky's platform",
          techUsed: "Vue, HTML, CSS, Bootstrap",
          githubLink: "",
          siteLink: "https://hartwell.co.uk",
          adobeXDLink: "",
          codepenLink: ""
        },
        {
          name: "Animation Reveal JS",
          image: "anim-reveal",
          desc:
            "Javascript exercise to simulate what wow.js does, add classes to elements on scroll, very basic approach without mutation observer.",
          techUsed: "Vanilla JS, HTML, CSS",
          githubLink: "",
          siteLink: "https://github.com/alextana/Reveal-Animation-JS",
          adobeXDLink: "",
          codepenLink: "https://codepen.io/alex-tana/pen/RzEJga"
        },

        {
          name: "Dreamplay Landing",
          image: "dreamplay-landing",
          desc: "Landing page for a startup project in the videogame industry",
          techUsed: "HTML, CSS, Bootstrap, Vanilla JS",
          githubLink: "",
          siteLink: "https://dreamplay.netlify.app/",
          adobeXDLink: "",
          codepenLink: ""
        },
        {
          name: "Dreamplay UX",
          image: "dreamplay",
          desc: "Adobe XD Concept for a social gaming platform",
          techUsed: "Adobe XD",
          githubLink: "",
          siteLink: "",
          adobeXDLink:
            "https://xd.adobe.com/view/5594969d-a9e0-4344-4dff-998615606567-23a5/?fullscreen",
          codepenLink: ""
        },
        {
          name: "Imaginix Landing",
          image: "imaginix-landing",
          desc: "Landing page for a videogame that was in development in 2013",
          techUsed: "HTML, CSS, Bootstrap, Vanilla JS",
          githubLink: "",
          siteLink: "https://imaginix-landing.netlify.app/",
          adobeXDLink: "",
          codepenLink: ""
        }
      ]
    };
  }
};
</script>

<style>
.desc {
  min-height: 7vh;
}
.card {
  background: #242424;
}
</style>
