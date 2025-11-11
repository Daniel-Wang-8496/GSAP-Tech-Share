<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { onMounted } from "vue";
import SplashGsap from './components/SplashGsap.vue'
import EasingGsap from "./components/EasingGsap.vue";

gsap.registerPlugin(ScrollTrigger);

// Initialize animations after DOM is loaded
onMounted(() => {
  gsap.utils.toArray('.reveal-text').forEach(elem => {
      gsap.from(elem, {
          duration: 1,
          opacity: 0,
          y: 40,
          ease: "power2.out",
          scrollTrigger: {
              trigger: elem,
              start: "top 85%",
              toggleActions: "play none none none"
          }
      });
  });


  gsap.from(".about-card", {
      duration: 0.8,
      opacity: 0,
      y: 50,
      stagger: 0.2,
      ease: "power2.out",
      scrollTrigger: {
          trigger: "#about",
          start: "top 70%",
          toggleActions: "play none none none"
      }
  });

  const card1 = document.querySelector("#card-1");
  card1.addEventListener("click", () => {
    gsap.to(card1, {
      backgroundColor: "#555555",
      color: "#aaaaaa",
      duration: 2
    });
  });

  const card2 = document.querySelector("#card-2");
  card2.addEventListener("click", () => {
    gsap.from(card2, {
      backgroundColor: "#555555",
      color: "#aaaaaa",
      duration: 2
    });
  });

  const card3 = document.querySelector("#card-3");
  card3.addEventListener("click", () => {
    gsap.fromTo(card3,
    { backgroundColor: "#555555", color: "#aaaaaa", duration: 2 },
    { backgroundColor: "black", color: "green", duration: 2 }
    );
  });

  const box = document.querySelector(".box");
  const tween = gsap.to(box, {
    x: "80%",
    rotation: 360,
    duration: 2,
    ease: "linear",
    paused: true
  });


  // click handlers for control methods
  document.querySelector("#play").onclick = () => tween.play();
  document.querySelector("#pause").onclick = () => tween.pause();
  document.querySelector("#resume").onclick = () => tween.resume();
  document.querySelector("#reverse").onclick = () => tween.reverse();
  document.querySelector("#restart").onclick = () => tween.restart();
  document.querySelector("#fast").onclick = () => tween.timeScale(2);
  document.querySelector("#slow").onclick = () => tween.timeScale(0.5);
  document.querySelector("#normal").onclick = () => tween.timeScale(1);
});
</script>

<template>
  <header>
  </header>
  <SplashGsap />
  <main>

  <div id="about">
      <div class="container">
          <h2 class="reveal-text">What To Do</h2>
          <div class="about-grid pure-g">
              <div class="pure-u-1 pure-u-md-1-3">
                <div class="about-card" id="card-1">
                    <h3>Homework</h3>
                    <p>CSCI 5117 Homework 2</p>
                </div>
              </div>

              <div class="pure-u-1 pure-u-md-1-3">
                <div class="about-card" id="card-2">
                    <h3>Chores</h3>
                    <p>Do Laundry</p>
                </div>
              </div>

              <div class="pure-u-1 pure-u-md-1-3">
                <div class="about-card" id="card-3">
                    <h3>Clubs</h3>
                    <p>Go to CASA Meeting</p>
                </div>
              </div>

              <div class="pure-u-1">
                <div class="about-card">
                  <div class="box"></div>
                </div>
              </div>

              <div class="control-methods">
                <button id="play">Play</button>
                <button id="pause">Pause</button>
                <button id="resume">Resume</button>
                <button id="reverse">Reverse</button>
                <button id="restart">Restart</button>
                <button id="fast">Fast</button>
                <button id="slow">Slow</button>
                <button id="normal">Normal</button>
              </div>

          </div>
      </div>
  </div>
  <div>
      <EasingGsap/>
  </div>

  </main>
</template>

<style scoped>

#about {
  color: white;
}

.reveal-text {
  margin-top: 2em;
}

.about-card {
  background: black;
  border-radius: 0.75rem;
  padding: 2rem;
  margin: 1rem;
  text-align: center;
}

.reveal-text {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 3rem;
}

</style>
