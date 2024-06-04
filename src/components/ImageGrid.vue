<template>
  <div class="image-grid">
    <div
        v-for="(image, index) in images"
        :key="index"
        class="image-item"
        @click="showImageDetails(image)"
    >
      <img :src="image.url" :alt="image.title" />
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
  images: {
    type: Array,
    required: true
  }
});

const emit = defineEmits(['image-selected']);

const showImageDetails = (image) => {
  emit('image-selected', image);
};
</script>

<style scoped>
.image-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.image-item {
  flex: 1 1 calc(33.333% - 10px);
  cursor: pointer;
}
.image-item img {
  width: 100%;
  height: auto;
  display: block;
}
@media (max-width: 600px) {
  .image-item {
    flex: 1 1 calc(50% - 10px);
  }
}
</style>
