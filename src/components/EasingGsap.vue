<script setup>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ref } from 'vue';
const state = ref(false);

onMounted(() => {
  gsap.set(".box", { x: 0 });
});

function animateBoxBase() {
  if(state.value==false){
    gsap.killTweensOf('.box');
    gsap.to('.box', { x: 500, backgroundColor: 'red'});
  }
  else if(state.value==true){
    gsap.killTweensOf('.box');
    gsap.to('.box', { x: 0, backgroundColor: 'blue'});
  }
  state.value = !state.value;
}

function animateBoxSnap() {
  if(state.value==false){
    gsap.set('.box', { x: 500, backgroundColor: 'red'});
  }
  else if(state.value==true){
    gsap.set('.box', { x: 0, backgroundColor: 'blue'});
  }
  state.value = !state.value;
}
</script>

<template>
  <div class="box"></div>
  <br/>
  <div>
    <button @click="animateBoxBase">Base Move</button>
    <button @click="animateBoxSnap">Snap Move</button>
  </div>
</template>

<style scoped>
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
