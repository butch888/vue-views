<script setup>
import ReviewListItem from './ReviewListItem.vue'

defineProps({
  filteredReviews: {
    type: Array,
    required: true,
  },
  removeReview: {
    type: Function,
    required: true,
  },
  toggleLike: {
    type: Function,
    required: true,
  },
})
</script>

<template>
  <!-- Список отзывов -->
  <ul class="review-tiles">
    <li v-for="(review, index) in filteredReviews" :key="review.id" class="review-tiles__item">
      <div class="review">
        <div class="review__header">
          <p class="review__author">{{ review.author }}</p>
        </div>
        <p class="review__text">"{{ review.text }}"</p>
      </div>
      <ReviewListItem
        :index="index"
        :toggle-like="toggleLike"
        :remove-review="removeReview"
        :review="review"
      />
    </li>

    <li v-if="filteredReviews.length === 0" class="reviews-tiles__item reviews-tiles__item--empty">
      <p>Нет отзывов по выбранному фильтру.</p>
    </li>
  </ul>
</template>

<style scoped>
.btn {
  border: none;
  cursor: pointer;
  border-radius: 4px;
}
.review-tiles {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
  gap: 1rem;
  padding: 0;
}

.review-tiles__item {
  flex-basis: calc(100% / 3 - 5rem);
  border: 1px solid #bebcbd;
  border-radius: 10px;
  padding: 1rem 2rem;
}

.reviews-tiles__item--empty {
  text-align: center;
  padding: 1rem;
  font-style: italic;
  color: #777;
}

@media screen and (max-width: 850px) {
  .review-tiles__item {
    flex-basis: calc(100% - 2rem);
  }
}

.review__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
  margin-bottom: 1rem;
}

.review__text {
  color: #807d7e;
  margin-bottom: 1.5rem;
}

.review__author {
  font-weight: bold;
  margin-bottom: 0.3rem;
}

.btn--like,
.btn--delete {
  padding: 4px 10px;
}

.btn--like {
  background: #f9f9f9;
}

.btn--delete {
  background: #ffdddd;
}
</style>
