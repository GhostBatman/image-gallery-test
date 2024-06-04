<template>
  <div id="app">
    <upload-form @files-selected="handleFiles" />
    <image-grid :images="state.images" @image-selected="selectImage" />
    <image-modal v-if="state.selectedImage" :image="state.selectedImage" @close="closeModal" />
  </div>
</template>

<script setup>
import { reactive } from 'vue';
import UploadForm from './components/UploadForm.vue';
import ImageGrid from './components/ImageGrid.vue';
import ImageModal from './components/ImageModal.vue';

const state = reactive({
  images: [],
  selectedImage: null
});

const handleFiles = (files) => {
  Array.from(files).forEach(file => {
    const reader = new FileReader();
    reader.onload = (e) => {
      state.images.push({
        url: e.target.result,
        title: file.name,
        description: '',
        date: new Date().toLocaleString()
      });
    };
    reader.readAsDataURL(file);
  });
};

const selectImage = (image) => {
  state.selectedImage = image;
};

const closeModal = () => {
  state.selectedImage = null;
};
</script>

<style>
#app {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
</style>
