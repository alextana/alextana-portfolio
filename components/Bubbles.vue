<template>
  <div class="particle__canvas"><div class="particles"></div></div>
</template>

<script>
export default {
  methods: {
    createParticles({
      // default values
      particleNumber = 40,
      particleSize = 35,
      colors = {
        firstColor: "#fff",
        secondColor: false,
      },
      randomizeSize = true,
      particleBorderRadius = 50,
      randomizeOpacity = true,
      randomizeColors = true,
      animation = "float",
      animationDuration = 20,
      animationLoop = true,
      blobs = false,
    }) {
      let particles,
        singleParticle,
        particleCanvas,
        canvasHeight,
        canvasWidth,
        singleParticleElement,
        particleStyle,
        particleTop,
        particleLeft,
        particleOpacity,
        randomSize,
        letters,
        color,
        animatedParticle,
        isFinished;

      // create particles
      particles = document.querySelector(".particles");
      for (let i = 0; i < particleNumber; i++) {
        singleParticle = document.createElement("div");
        singleParticle.classList.add("particle__element");
        particles.appendChild(singleParticle);
      }

      // get canvas and set width/height
      particleCanvas = document.querySelector(".particle__canvas");
      singleParticleElement = document.querySelectorAll(".particle__element");
      canvasHeight = particleCanvas.clientHeight;
      canvasWidth = particleCanvas.clientWidth;

      // apply styles to the single particles
      for (let x = 0; x < singleParticleElement.length; x++) {
        particleStyle = singleParticleElement[x].style;
        particleTop = Math.floor(Math.random() * canvasHeight);
        particleLeft = Math.floor(Math.random() * canvasWidth);
        particleOpacity = Math.random();
        particleStyle.position = "absolute";
        // helper function to create min/max random values for blob radius
        function randomNumberHundredBlob() {
          // sweet spot for blob looking circles
          return Math.floor(Math.random() * (100 - 40) + 40);
        }
        if (blobs) {
          particleStyle.borderRadius = `
            ${randomNumberHundredBlob()}% ${randomNumberHundredBlob()}% 
            ${randomNumberHundredBlob()}% ${randomNumberHundredBlob()}%
            `;
        } else {
          particleStyle.borderRadius = particleBorderRadius + "%";
        }

        particleStyle.top = particleTop + "px";
        particleStyle.left = particleLeft + "px";

        // randomize opacity conditional -- start
        randomizeOpacity
          ? (particleStyle.opacity = particleOpacity)
          : (particleStyle.opacity = 1);
        if (particleSize) {
          particleStyle.width = particleSize + "px";
          particleStyle.height = particleSize + "px";
        }
        // randomize opacity conditional -- end

        // randomize size conditional -- start
        if (randomizeSize) {
          randomSize = Math.floor(Math.random() * particleSize);
          particleStyle.width = randomSize + "px";
          particleStyle.height = randomSize + "px";
        }
        // randomize size conditional -- end

        // randomize colors conditional -- start
        if (randomizeColors) {
          letters = "0123456789ABCDEF";
          color = "#";
          for (var y = 0; y < 6; y++) {
            color += letters[Math.floor(Math.random() * 16)];
          }
          particleStyle.background = color;
        }
        // alternate the particles colors to have first / second
        // they're split in half checking the modulus of 2
        // only if secondColor is defined
        else if (colors.secondColor) {
          x % 2 === 0
            ? (particleStyle.background = colors.firstColor)
            : (particleStyle.background = colors.secondColor);
        }
        // otherwise only set first color
        else {
          particleStyle.background = colors.firstColor;
        }
        // randomize colors conditional -- end

        // animate function -- start
        if (animation !== "none") {
          animate();
          function animate() {
            // float animation + blobs animation
            if (animation === "float" || animation === "blobs") {
              setTimeout(function animateParticles() {
                isFinished = false;
                let randomAnimationDuration =
                  Math.floor(Math.random() * animationDuration) +
                  animationDuration / 2;
                animatedParticle = singleParticleElement[x].style;
                if (isFinished === false) {
                  animatedParticle.top =
                    Math.floor(Math.random() * canvasHeight) + "px";
                  animatedParticle.left =
                    Math.floor(Math.random() * canvasWidth) + "px";
                  // float animation
                  if (animation === "float") {
                    animatedParticle.transition = `${randomAnimationDuration}s top ease-in-out, ${randomAnimationDuration}s left ease-in-out`;
                  }
                  // blobs animation
                  if (animation === "blobs") {
                    animatedParticle.transition = `
                            ${randomAnimationDuration}s border-radius ease-in-out, ${randomAnimationDuration}s top ease-in-out, ${randomAnimationDuration}s left ease-in-out`;
                    animatedParticle.borderRadius = `
                            ${randomNumberHundredBlob()}% ${randomNumberHundredBlob()}% 
                            ${randomNumberHundredBlob()}% ${randomNumberHundredBlob()}%
                            `;
                  }
                }
                // loop animation only if set up
                if (animationLoop === true) {
                  setTimeout(() => {
                    isFinished = true;
                    if (isFinished === true) {
                      singleParticleElement[x].style.top =
                        Math.floor(Math.random() * canvasHeight) + "px";
                      singleParticleElement[x].style.left =
                        Math.floor(Math.random() * canvasWidth) + "px";
                      isFinished = false;
                      animateParticles();
                    }
                  }, randomAnimationDuration * 1000);
                }
              }, 1);
            }
          }
        }
        // animate function -- end
      }
    },
  },
  mounted() {
    this.createParticles({
      particleNumber: 55,
      particleSize: 15,
      randomizeSize: true,
      randomizeColors: false,
      particleBorderRadius: 50,
      blobs: false,
      randomizeOpacity: true,
      colors: {
        firstColor: "#27fb6b",
        secondColor: "#27fb6b",
      },
      animation: "float",
      animationDuration: 20,
      animationLoop: true,
    });
  },
};
</script>
<style>
@media (max-width: 768px) {
  .particle__element {
    filter: blur(10px);
  }
}

.particle__canvas {
  pointer-events: none;
  background: #0a2e36;
  overflow: hidden;
  position: relative;
  width: 100%;
  height: 100vh;
  margin: 0;
}
</style>