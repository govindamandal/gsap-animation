<template>
  <div class="parent">
    <div class="red">
      <h1>RED CLASS</h1>
    </div>
    <div v-if="products" class="green products flex-inline">
      <div v-for="product in products" :key="product.id"
        class="relative m-8 flex max-w-xs flex-col overflow-hidden rounded-lg border border-gray-100 bg-white shadow-md float-left">
        <a class="relative mx-1 mt-1 flex h-60 overflow-hidden rounded-xl" href="#">
          <img class="object-cover" :src="product.image" :alt="product.title" />
          <span
            class="absolute top-0 left-0 m-2 rounded-full bg-black px-2 text-center text-sm font-medium text-white" :ref="`discount${product.id}`">39%
            OFF</span>
        </a>
        <div class="mt-4 px-5 pb-5">
          <a href="#">
            <h5 class="text-xl tracking-tight text-slate-900">{{ product.title }}</h5>
          </a>
          <div class="mt-2 mb-5 flex items-center justify-between">
            <p>
              <span class="text-3xl font-bold text-slate-900 text-center">{{ product.price }}</span>
            </p>
          </div>
          <a href="#"
            class="flex items-center justify-center rounded-md bg-slate-900 px-5 py-2.5 text-center text-sm font-medium text-white hover:bg-gray-700 focus:outline-none focus:ring-4 focus:ring-blue-300">
            <svg xmlns="http://www.w3.org/2000/svg" class="mr-2 h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
            </svg>
            Add to cart</a>
        </div>
      </div>
    </div>
  </div>
</template>
<script>

import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

export default {
  data() {
    return {
      products: []
    }
  },
  created() {
    this.loadProducts();
  },
  mounted() {
    gsap.registerPlugin(ScrollTrigger);
    setTimeout(() => {
      this.products.map((product) => {
        const element = this.$refs[`discount${product.id}`]
        console.log('element ', element);
        gsap.to(element, {
          scrollTrigger: {
            trigger: element,
            start: 'top center'
          },
          duration: 3,
          y: 300
        })
      })
    }, 1100);
  },
  methods: {
    loadProducts() {
      fetch('https://fakestoreapi.com/products').then((response) => response.json().then((data) => {
        this.products = data;
      }))
    }
  }
}

</script>