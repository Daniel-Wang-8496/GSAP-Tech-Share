<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { onMounted } from "vue";
import SplashGsap from './components/SplashGsap.vue'

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
});
</script>

<template>
  <header>
  </header>
  <SplashGsap />
  <main>
    <div style="height: 100vh; display: flex; align-items: center; justify-content: center;">
      Scroll down to see the animation
    </div>

  <!-- idk what cards could be. some features, values, etc. -->
  <div id="about">
      <div class="container">
          <h2 class="reveal-text">What To Do</h2>
          <div class="about-grid pure-g">
              <div class="pure-u-1 pure-u-md-1-3">
                <div class="about-card">
                    <h3>Homework</h3>
                    <p>Test1</p>
                </div>
              </div>

              <div class="pure-u-1 pure-u-md-1-3">
                <div class="about-card">
                    <h3>Chores</h3>
                    <p>Test2</p>
                </div>
              </div>
              
              <div class="pure-u-1 pure-u-md-1-3">
                <div class="about-card">
                    <h3>Clubs</h3>
                    <p>Test3</p>
                </div>
              </div>
          </div>
      </div>
  </div>


  </main>
</template>

<style scoped>

#about {
  color: white;
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