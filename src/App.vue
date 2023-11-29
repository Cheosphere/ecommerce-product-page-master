<script setup>
import { ref, onMounted, onUnmounted, onBeforeUnmount } from 'vue'
import Header from './components/Header.vue'
import Gallery from './components/Gallery.vue'
import Content from './components/Content.vue'
import Lightbox from './components/Lightbox.vue'

const count = ref(0)
const total = ref(0)

function countReceived(data) {
  count.value += data
  total.value = count.value * 125
}

function reset() {
  total.value = 0
  count.value = 0
}

const lightbox = ref(null)
const status = ref(true)

const disabledFunction = () => {
  if (window.innerWidth < 680) {
    status.value = false
  } else {
    status.value = true
  }
}

function showGallery(data) {
  if (data) {
    lightbox.value.style.display = 'flex'
  }
}

function closeGallery() {
  lightbox.value.style.display = 'none'
}

// Close Lightbox with Escape key
const closeWindowOnEscape = (event) => {
  if (event.key === 'Escape') {
    lightbox.value.style.display = 'none'
  }
}

onMounted(() => {
  disabledFunction()
  window.addEventListener('resize', disabledFunction)
  // Add the event listener when mounting the component
  window.addEventListener('keydown', closeWindowOnEscape)
});

onUnmounted(() => {
  // Remove the event listener when mounting the component
  window.removeEventListener('keydown', closeWindowOnEscape)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', disabledFunction)
})

</script>

<template>
  <Header @countReset="reset" :counter="count" :total="total" />
  <main class="main-content">
    <Gallery @showLightbox="showGallery(status)"/>
    <Content @countRegistered="countReceived" />
  </main>
  <section class="lightbox" ref="lightbox">
    <transition>
      <Lightbox @closeLightbox="closeGallery" />
    </transition>
  </section>
</template>

<style scoped>
.main-content {
  width: 100%;
  max-width: 1014px;
  height: 787px;
  display: flex;
  justify-content: space-between;
  transition: .2s;
}
.lightbox {
    width: 100%;
    height: 100%;
    display: none;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 0;
    background-color: rgba(0, 0, 0, 0.8);
    z-index: 200;
}

/* Media Query */
@media screen and (max-width: 1080px) {
  .main-content {
    padding: 0 2rem;
  }
}

@media screen and (max-width: 880px) {
  .main-content {
    flex-direction: column;
    align-items: center;
  }
}

@media screen and (max-width: 680px) {
  .main-content {
    padding: 0;
  }
  .lightbox {
    width: 0;
  }
}
</style>
