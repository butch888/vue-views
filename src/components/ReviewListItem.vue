<script setup>
defineProps({
  index: Number,
  review: Object,
  toggleLike: Function,
  removeReview: Function,
})
</script>

<template>
  <div class="review__rating">
    <span v-for="n in 5" :key="`star-${n}`" class="star">
      {{ n <= review.rating ? '★' : '☆' }}
    </span>
  </div>
  <div class="review__actions">
    <button @click="toggleLike(review)" class="btn btn--like">
      {{ review.liked ? '❤️' : '🤍' }}
    </button>
    <button @click="removeReview(index)" class="btn btn--delete">Удалить</button>
  </div>
</template>

<style scoped>
.review__rating {
  color: gold;
  font-size: 1.2rem;
}

.review__actions {
  display: flex;
  gap: 10px;
}
</style>
