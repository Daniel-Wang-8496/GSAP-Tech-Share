<script setup>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  const tl = gsap.timeline();
  tl.from(".white", { xPercent: -100 })
    .from(".black", { xPercent: 100 })
    .from(".gray", { yPercent: -100 });

  ScrollTrigger.create({
    animation: tl,
    trigger: "#container",
    start: "top top",
    end: "+=4000",
    scrub: true,
    pin: true,
    anticipatePin: 1,
  });
});
</script>

<template>
  <div id="container">
    <section class="white"><p>To</p></section>
    <section class="black"><p>Do</p></section>
    <section class="gray"><p>List</p></section>
  </div>
</template>

<style scoped>
#container {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  position: relative;
}


.white,
.black,
.gray {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 4rem;
  width: 100vw;;
  height: 100vh;
  position: absolute; /* stack them on top of each other */
  top: 0;
  left: 0;
}

.white {
  background-color: white;
  color: black;
}

.black {
  background-color: black;
  color: white;
}

.gray {
  background-color: gray;
  color: white;
}
</style>