<template>
    <div class="parent">
      <div class="red"></div>
      <div class="green">
        <div class="square"></div>
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
          trigger: '.square',
          start: 'top 60%',
          end: 'top 40%',
          toggleActions: 'restart pause resume          none',
          //              onEnter onLeave onEnterBack   onLeaveBack
          markers: {
            startColor: 'purple',
            endColor: 'fuchsia',
            fontSize: '3rem'
          }
        },
        duration: 3,
        x: 700
      })
    }
  }
  </script>