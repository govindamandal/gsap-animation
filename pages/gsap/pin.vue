<template>
    <div class="parent">
      <div class="red"></div>
      <div class="green">
        <div class="square"></div>
        <div class="square2"></div>
      </div>
    </div>
  </template>
  <script>
  import { gsap } from 'gsap';
  import { ScrollTrigger } from 'gsap/ScrollTrigger';
  
  gsap.registerPlugin(ScrollTrigger);
  
  export default {
    mounted() {
      gsap.to('.square', {
        scrollTrigger: {
          trigger: '.square2',
          start: 'top 80%',
          end: 'top 30%',
          scrub: 4,
          pin: '.square',
          pinSpacing: true,
          toggleActions: 'restart none none none',
          //              onEnter onLeave onEnterBack   onLeaveBack
          markers: {
            startColor: 'purple',
            endColor: 'fuchsia',
            fontSize: '3rem'
          }
        },
        duration: 3,
        // x: 700
      })
    }
  }
  </script>