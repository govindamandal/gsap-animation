<template>
    <div class="parent">
        <div class="panel"></div>
        <div class="box"></div>
        <div class="panel"></div>
    </div>
</template>
<script>
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

  gsap.registerPlugin(ScrollTrigger);

export default {
    mounted() {
        //   gsap.to('.box', { x: 500, duration: 5 })
        //   gsap.to('.box', { y: 300, duration: 3, delay: 2 })
        //   gsap.to('.box', { x: 0, duration: 2, delay: 5 })

        const tl = gsap.timeline({
            scrollTrigger: {
                trigger: '.box',
                markers: true,
                start: 'top 80%',
                end: 'top 30%',
                scrub: true,
            }
        });

        tl.to('.box', { x: 500, duration: 5 })
            .to('.box', { y: 200, duration: 2 })
            .to('.box', { x: 0, duration: 2 })
    }   
}
</script>