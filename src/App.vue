<script setup>
import { ref, onMounted } from 'vue'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faPhone } from "@fortawesome/free-solid-svg-icons/faPhone"
import { faBars } from "@fortawesome/free-solid-svg-icons/faBars"
import BookBtn from '@/components/home/BookBtn.vue'
import { RouterLink, RouterView } from 'vue-router'
import { useRouter } from 'vue-router';

const navActive = ref(false)

const  toggleNavBar = ()=> {
    navActive.value = !navActive.value
    console.log('clicked');
  }

const router = useRouter();

onMounted(() => {
  router.beforeEach(() => {
    navActive.value = false;
    return true; // Allow the navigation
  });
});

</script>

<template>
  <header class="bg-cyan-950 p-4 font-mono fixed top-0 left-0 z-50 w-full md:p-2">
    <nav class="w-11/12 mx-auto flex justify-between items-center gap-">
      <div class="nav-logo w-1/6 md:w-1/12 z-10">
        <router-link to="/"><img src="./assets/pearlygates/logo-removebg-preview.png" alt="logo" class=""></router-link>
      </div>
      <div class="links">
        <div class="contact flex items-center justify-start md:justify-end gap-3">
          <p class="text-white p-2"><a href="tel:+23470876680366" class="hover:underline"><FontAwesomeIcon :icon="faPhone" class="bg-slate-800 p-3 rounded-full md:border-0 md:p-0 md:bg-transparent"/> <span class="hidden md:inline">+23470876680366</span> </a></p>
          <BookBtn class=""/>
          <!-- <router-link to="/booking"><button class="rounded-full bg-orange-600 p-2 text-white text-sm md:p-3">BOOK NOW</button></router-link> -->
        </div>
        <div :class="['nav-links md:flex md:items-center text-white bg-cyan-950/90 md:bg-transparent h-screen md:h-0 w-6/12 md:w-full left-0 top-14 md:top-0 pt-10 px-4 md:p-4 md:gap-8 mt-5 absolute md:relative md:block', {hidden: !navActive}]">
          <router-link class="block my-5 p-2 rounded-md hover:bg-white hover:text-cyan-950 transition-all duration-500 md:inline"to="/">HOME</router-link>
          <router-link class="block my-5 p-2 rounded-md hover:bg-white hover:text-cyan-950 transition-all duration-500 md:inline"to="/rooms">ROOMS</router-link>
          <router-link class="block my-5 p-2 rounded-md hover:bg-white hover:text-cyan-950 transition-all duration-500 md:inline"to="/gallery">GALLERY</router-link>
          <router-link class="block my-5 p-2 rounded-md hover:bg-white hover:text-cyan-950 transition-all duration-500 md:inline"to="/about-us">ABOUT US</router-link>
          <router-link class="block my-5 p-2 rounded-md hover:bg-white hover:text-cyan-950 transition-all duration-500 md:inline"to="/contact">CONTACT US</router-link>
        </div>
        
      </div>
      <div class="menu-bar relative mx-2 right-0 md:hidden"  @click="toggleNavBar">
          <FontAwesomeIcon class="text-white text-2xl":icon="faBars" />
      </div>
    </nav>
  </header>
  

  <RouterView />
</template>

<style scoped>

</style>
