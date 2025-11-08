<script setup>
    import { gsap } from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    gsap.registerPlugin(ScrollTrigger);

    const tl = gsap.timeline();
    tl.from(".white", {xPercent: -100}).from(".black", {xPercent: 100}).from(".gray", {yPercent:-100})

    ScrollTrigger.create({
        animation: tl,
        trigger: "#container",
        start: "top top",
        end: "+=4000",
        scrub: true,
        pin: true,
        anticipatePin: 1
    })
</script>

<template>
  <h2>Welcome to your todolist!</h2>
  <div id="container">
    <div class="white"><p>1</p></div>
    <div class="black"><p>2</p></div>
    <div class="gray"><p>3</p></div>
  </div>

</template>

<style scoped>
.white{
    background-color: white;
}
.black{
    background-color: black;
}
.black, p{
    color: white
}
.gray{
    background-color: gray;
}
</style>
