<script setup>
import Hero from '@/components/Hero.vue';
import HomeCard from '@/components/HomeCard.vue';
import JobListings from '@/components/JobListings.vue';
</script>

<template>
    <!-- <Hero title='test title' subtitle ='subtitle test'/> -->
  <Hero/>
<HomeCard/>
<JobListings :limit="3" />
</template>
