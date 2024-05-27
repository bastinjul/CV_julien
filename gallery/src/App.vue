<script setup lang="ts">
import {ref} from 'vue';

const photoPaths = Object.keys(import.meta.glob('/public/photos/*', { import: 'default', eager: true }));
const photos = ref(photoPaths.map(path => {
  return {
    path: window.document.location.href + path,
    alt: 'photo'
  }
}))
const responsiveOptions = ref([
  {
    breakpoint: '1500px',
    numVisible: 5
  },
  {
    breakpoint: '1024px',
    numVisible: 3
  },
  {
    breakpoint: '768px',
    numVisible: 2
  },
  {
    breakpoint: '560px',
    numVisible: 1
  }
]);
const display = ref(true)
</script>

<template>
  <div class="card flex justify-content-center">
    <Galleria v-model:visible="display" :value="photos" :responsiveOptions="responsiveOptions" :num-visible="9" :circular="true" :showItemNavigators="true" containerStyle="max-width: 50%" :fullScreen="true" :showThumbnails="false">
      <template #item="slotProps">
        <img :src="slotProps.item.path" style="width: 100%; display: block;"  :alt="slotProps.item.alt"/>
      </template>
      <template #thumbnail="slotProps">
        <img :src="slotProps.item.path" :alt="slotProps.item.alt" style="display: block;" />
      </template>
    </Galleria>
    <Button label="Voir les photos" icon="pi pi-external-link" @click="display = true" />
  </div>
</template>

<style scoped>
  body #app header {
    margin: 0;
    padding: 0;
  }
  header {
    display:flex;
    align-items:center;
    justify-content:center;
  }
</style>