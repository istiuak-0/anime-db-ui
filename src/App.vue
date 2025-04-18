<script setup lang="ts">
import Card from "./components/Card.vue"
import { ref } from "vue";
import axios from "axios";

const searchQuery=ref<string>('')
const animeList=ref([]);



const HandleSearch=async () => {
  let animeData=await axios.get(`https://api.jikan.moe/v4/anime?q=${searchQuery.value}`)
animeList.value=animeData.data.data

}

</script>

<template>
  <div class="app">
    <!-- header -->
    <header>
      <h1>The <b>Anime</b> Database</h1>
      <!-- search field -->
      <form class="search-box" @submit.prevent="HandleSearch">
        <input required type="search" class="search-field" placeholder="Search for an anime.." v-model="searchQuery">
      </form>

    </header>

    <main>

      <div class="cards" v-if="animeList.length>0">
        <Card v-for=" anime in animeList" :key="anime.mal_id" :anime />
      </div>
    </main>
  </div>
</template>
