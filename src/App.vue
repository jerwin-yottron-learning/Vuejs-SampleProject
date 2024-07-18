<script setup>
import NavBar from './components/NavBar.vue';
import Hero from './components/Hero.vue';
import HomeCard from '@/components/HomeCard.vue';
import JobListings from '@/components/JobListings.vue';
</script>
<template>
  <NavBar/>
  <!-- <Hero title='test title' subtitle ='subtitle test'/> -->
  <Hero/>
<HomeCard/>
<JobListings/>
</template>