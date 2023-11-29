<script setup>
import { ref, onMounted, onBeforeUnmount  } from 'vue';
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue'
// Import Swiper styles
import 'swiper/css'
import 'swiper/css/free-mode'
import 'swiper/css/navigation'
import 'swiper/css/thumbs'
// import required modules
import { FreeMode, Navigation, Thumbs } from 'swiper/modules'

const thumbsSwiper = ref(null)

const setThumbsSwiper = (swiper) => {
    thumbsSwiper.value = swiper
}

const nav = ref(false)

const viewport = () => {
  if (window.innerWidth < 681) {
    nav.value = true
  } else {
    nav.value = false
  }
}

onMounted(() => {
    viewport();
    window.addEventListener('resize', viewport)
})

onBeforeUnmount(() => {
    window.removeEventListener('resize', viewport)
})

const modules = [FreeMode, Navigation, Thumbs]

const emit = defineEmits(['showLightbox'])

const lightbox = () => {
    emit('showLightbox')
}

</script>

<template>
    <section class="container">
        <swiper @click="lightbox"
            :loop="true"
            :spaceBetween="5"
            :navigation="nav"
            :grabCursor="true"
            :thumbs="{ swiper: thumbsSwiper }"
            :modules="modules"
            class="mySwiper2"
        >
            <swiper-slide><img class="product-img" src="../assets/images/image-product-1.jpg" /></swiper-slide>
            <swiper-slide><img class="product-img" src="../assets/images/image-product-2.jpg" /></swiper-slide>
            <swiper-slide><img class="product-img" src="../assets/images/image-product-3.jpg" /></swiper-slide>
            <swiper-slide><img class="product-img" src="../assets/images/image-product-4.jpg" /></swiper-slide>
        </swiper>
        <swiper
            @swiper="setThumbsSwiper"
            :loop="true"
            :spaceBetween="31"
            :slidesPerView="4"
            :freeMode="true"
            :watchSlidesProgress="true"
            :modules="modules"
            class="mySwiper"
        >
            <swiper-slide><img src="../assets/images/image-product-1-thumbnail.jpg" /></swiper-slide>
            <swiper-slide><img src="../assets/images/image-product-2-thumbnail.jpg" /></swiper-slide>
            <swiper-slide><img src="../assets/images/image-product-3-thumbnail.jpg" /></swiper-slide>
            <swiper-slide><img src="../assets/images/image-product-4-thumbnail.jpg" /></swiper-slide>
        </swiper>
    </section>
</template>

<style scoped>
.container {
    width: 50%;
    max-width: 445px;
    height: fit-content;
    margin-top: 5.65rem;
    z-index: 9;
}
.swiper:nth-child(2) {
    width: 100.8%;
    padding-left: 2px;
    padding-bottom: 2px;
    padding-right: 3px;
    left: -2px;
}
.swiper-slide .product-img {
    width: 100%;
    border-radius: .9rem;
}
.swiper:nth-child(2) .swiper-wrapper .swiper-slide {
    display: flex;
    margin-top: 1.7rem;
}
.swiper:nth-child(2) .swiper-wrapper .swiper-slide img {
    max-width: 88px;
    height: 88px;
    border-radius: .6rem;
    cursor: pointer;
    transition: .2s;
}
.swiper:nth-child(2) .swiper-wrapper .swiper-slide:hover img {
    opacity: .5;
}
.swiper:nth-child(2) .swiper-slide-thumb-active img {
    opacity: .25;
}
.swiper:nth-child(2) .swiper-slide-thumb-active::after {
    content: "";
    width: 88px;
    height: 88px;
    position: absolute;
    outline: 2px solid var(--orange);
    border-radius: .6rem;
    z-index: -1;
}

/* Media Query */
@media screen and (max-width: 960px) {
    .swiper:nth-child(2) {
        width: 100%;
    }
    .swiper:nth-child(2) .swiper-wrapper .swiper-slide img {
        width: 100%;
        height: 100%;
        margin: 0 auto;
        border-radius: .5rem;
    }
    .swiper:nth-child(2) .swiper-slide-thumb-active::after {
        width: 100%;
        height: 100%;
        border-radius: .5rem;
    }
}

@media screen and (max-width: 880px) {
    .container {
        width: 100%;
        max-width: 550px;
        margin-top: 2rem;
    }
    .swiper:nth-child(2) {
        padding-left: 5px;
    }
    .swiper:nth-child(2) .swiper-wrapper .swiper-slide {
        margin-top: 1rem;
    }
    .swiper:nth-child(2) .swiper-slide-thumb-active::after {
        content: "";
        width: 88px;
        height: 88px;
        margin: 0 .78rem;
        border-radius: .5rem;
    }

}

@media screen and (max-width: 680px) {
    .container {
        max-width: none;
        margin-top: 0;
    }
    .swiper-slide .product-img {
        border-radius: 0;
    }
    .swiper:nth-child(2) {
        display: none;
    }
    
}
</style>