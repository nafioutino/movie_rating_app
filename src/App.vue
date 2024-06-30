<script setup>
import { ref } from "vue";
import { items } from "./movies.json";

// Assurez-vous que items est réactif
const reactiveItems = ref(items);

function updateRating(itemIndex, rating) {
  // Mettre à jour la note de l'élément
  reactiveItems.value[itemIndex].rating = rating;
  // Ajouter ici la logique pour persister la nouvelle note si nécessaire
}

const starStyles = (item, star) => ({
  // Changer la couleur de remplissage des étoiles en fonction de la note
  fill: star <= item.rating ? "yellow" : "rgb(187, 177, 177)",
});
</script>

<template>
  <div class="container">
    <div v-for="(item, itemIndex) in reactiveItems" :key="item.id">
      <article>
        <img :src="item.image" alt="movie_image" srcset="" />
        <div class="details">
          <h2>{{ item.name }}</h2>
          <ul>
            <li v-for="genre in item.genres" :key="genre">{{ genre }}</li>
          </ul>
          <p>{{ item.description }}</p>
          <p>
            Rating:({{ item.rating + "/5" }})
            <button
              v-for="star in 5"
              :key="star"
              @click="updateRating(itemIndex, star)"
            >
              <svg
                :style="starStyles(item, star)"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="size-6"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M11.48 3.499a.562.562 0 0 1 1.04 0l2.125 5.111a.563.563 0 0 0 .475.345l5.518.442c.499.04.701.663.321.988l-4.204 3.602a.563.563 0 0 0-.182.557l1.285 5.385a.562.562 0 0 1-.84.61l-4.725-2.885a.562.562 0 0 0-.586 0L6.982 20.54a.562.562 0 0 1-.84-.61l1.285-5.386a.562.562 0 0 0-.182-.557l-4.204-3.602a.562.562 0 0 1 .321-.988l5.518-.442a.563.563 0 0 0 .475-.345L11.48 3.5Z"
                />
              </svg>
            </button>
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
img {
  width: 100%;
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
  font-size: 30px;
  padding: 15px;
  line-height: 2;
}

button {
  border: none;
  margin: 5px;
  cursor: pointer;
}

.size-6 {
  width: 35px;
}
</style>
