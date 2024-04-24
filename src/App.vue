<script setup>
import { ref } from "vue";
import { items } from "./movies.json";
/*
 This is an Icon that you can use to represent the stars if you like
 otherwise you could just use a simple ⭐️ emoji, or * character.
*/
import { StarIcon } from "@heroicons/vue/24/solid";
const movies = ref(items);
</script>

<template>
  <!-- This is where your template goes	-->
  <div class="flex p-10 gap-x-4">
    <div
      v-for="(movie, index) in movies"
      class="bg-white movie-card"
      :key="index"
    >
      <img :src="movie.image" :id="items.id" />
      <div class="flex flex-col p-4">
        <h2 class="title">{{ movie.name }}</h2>
        <div class="flex gap-x-1 mb-3">
          <div
            v-for="genre in movie.genres"
            :index="genre"
            class="genre rounded-xl bg-purple-300 px-3"
          >
            {{ genre }}
          </div>
        </div>
        <p class="description">{{ movie.description }}</p>
        <div class="flex rating items-center">
          <span class="mr-2">Rating: ({{ movie.rating }})/5: </span>
          <StarIcon v-for="n in movie.rating" class="star"></StarIcon>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.movie-card {
  width: 300px;
}
.genre {
  font-size: 12px;
}
.description {
  font-size: 14px;
}
.title {
  font-size: 20px;
}
.star {
  width: 20px;
  color: orange;
}
.rating {
  font-size: 12px;
}
</style>
