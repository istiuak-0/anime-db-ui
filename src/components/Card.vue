<script setup lang="ts">
import { defineProps } from 'vue';
const props=defineProps(["anime"])



</script>

<template>
  <div class="card">
    <a :href="anime.url" target="_blank">
      <img :src="anime.images.jpg.image_url">
      <h3>{{anime.title}}</h3>
    </a>
  </div>
</template>