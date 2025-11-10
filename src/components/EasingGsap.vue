<script setup>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ref } from 'vue';
const state = ref(false);

onMounted(() => {
  gsap.set(".box", { xPercent: 0 });
});

function animateBoxNoStagger() {
  if(state.value==false){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 500, backgroundColor: 'red'});
  }
  else if(state.value==true){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 0, backgroundColor: 'blue'});
  }
  state.value = !state.value;
}

function animateBoxBase() {
  if(state.value==false){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 500, backgroundColor: 'red', stagger: 0.2});
  }
  else if(state.value==true){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 0, backgroundColor: 'blue', stagger: 0.2});
  }
  state.value = !state.value;
}

function animateBoxSnap() {
  if(state.value==false){
    gsap.set('.box', { xPercent: 500, backgroundColor: 'red', stagger: 0.2});
  }
  else if(state.value==true){
    gsap.set('.box', { xPercent: 0, backgroundColor: 'blue', stagger: 0.2});
  }
  state.value = !state.value;
}

function animateBoxLong() {
  if(state.value==false){
    gsap.to('.box', { xPercent: 500, backgroundColor: 'red', duration: 3, stagger: 0.2});
  }
  else if(state.value==true){
    gsap.to('.box', { xPercent: 0, backgroundColor: 'blue', duration: 3, stagger: 0.2});
  }
  state.value = !state.value;
}

function animateBoxRoll() {
  if(state.value==false){
    gsap.to('.box', { xPercent: 500, backgroundColor: 'red', rotation:90, stagger: 0.2});
  }
  else if(state.value==true){
    gsap.to('.box', { xPercent: 0, backgroundColor: 'blue', rotation:0, stagger: 0.2});
  }
  state.value = !state.value;
}

function easingBounce() {
  if(state.value==false){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 500, backgroundColor: 'red', ease: "bounce.out", duration: 1.5, stagger: 0.2});
  }
  else if(state.value==true){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 0, backgroundColor: 'blue', ease: "bounce.out", duration: 1.5, stagger: 0.2});
  }
  state.value = !state.value;
}

function easingPower() {
  if(state.value==false){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 500, backgroundColor: 'red', ease: "power3.out", duration: 1.5, stagger: 0.2});
  }
  else if(state.value==true){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 0, backgroundColor: 'blue', ease: "power3.out", duration: 1.5, stagger: 0.2});
  }
  state.value = !state.value;
}

function easingSteps() {
  if(state.value==false){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 500, backgroundColor: 'red', ease: "steps(5)", duration: 1.5, stagger: 0.2});
  }
  else if(state.value==true){
    gsap.killTweensOf('.box');
    gsap.to('.box', { xPercent: 0, backgroundColor: 'blue', ease: "steps(5)", duration: 1.5, stagger: 0.2});
  }
  state.value = !state.value;
}

</script>

<template>
  <div id="container">
    <div class="box"></div>
    <br/>
    <div class="box"></div>
    <br/>
    <div class="box"></div>
    <br/>
    <div>
      <button @click="animateBoxBase">Base Move</button>
      <button @click="animateBoxSnap">Snap Move</button>
      <button @click="animateBoxLong">Long Move</button>
      <button @click="animateBoxRoll">Roll Move</button>
    </div>
    <div>
      <button @click="easingBounce">Bounce Ease</button>
      <button @click="easingPower">Power Ease</button>
      <button @click="easingSteps">Steps Ease</button>
    </div>
    <div>
      <button @click="animateBoxNoStagger">No Stagger</button>
    </div>
  </div>
</template>

<style scoped>
  #container {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    position: relative;
  }
  body {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    min-height: 100vh;
    margin: 0;
    overflow: hidden;
  }

  .box {
      width: 150px;
      height: 150px;
      transition: none;
      background-color: blue;
    }
</style>
