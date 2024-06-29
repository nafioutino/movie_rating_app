<script setup>
import { items } from "./movies.json";
/*
 This is an Icon that you can use to represent the stars if you like
 otherwise you could just use a simple ⭐️ emoji, or * character.
*/
import { StarIcon } from "@heroicons/vue/24/solid";
</script>

<template>
  <!-- This is where your template goes	-->
 
    <div class="container">
      <div v-for="item in items" :key="item.id"   >
        <article>
          <img :src="item.image" alt="movie_image" srcset="" />
          <div class="details">
            <h2>{{ item.name }}</h2>
            <ul>
              <li v-for="genre in item.genres" :key="genre">{{ genre }}</li>
            </ul>
            <p>{{ item.description }}</p>
            <p>
              Rating:({{ item.rating + '/5' }}) <span v-for="star in 5" :key="star" class="star">
                {{ star <= item.rating ? "⭐" : "☆" }}
              </span>
            </p>
          </div>
        </article>
    </div>
    </div>
  
</template>

<style scoped>

.container {
  width: 100%;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  
}

article {
display: inline-block;
 width: 500px;
 margin: 15px;

  
  
}
img  {
  width:100%;
  height: 700px;

}

li {
  display: inline-block;
  background-color: #8a8cf5;
  margin: 10px;
  color: white;
  padding: 5px;
  border-radius: 5px;
}

.details {
  background-color: #fff;
  font-size: 25px;
  padding: 15px;
  line-height:2;

}

</style>
