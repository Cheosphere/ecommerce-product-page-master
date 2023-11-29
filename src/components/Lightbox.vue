<script setup>
import { ref } from 'vue';
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

const modules = [FreeMode, Navigation, Thumbs]

const emit = defineEmits(['closeLightbox'])

const close = () => {
    emit('closeLightbox')
}

</script>

<template>
    <section class="container">
        <swiper
            :loop="true"
            :navigation="true"
            :spaceBetween="5"
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
        <svg @click="close" class="icon-close" width="14" height="15" xmlns="http://www.w3.org/2000/svg"><path d="m11.596.782 2.122 2.122L9.12 7.499l4.597 4.597-2.122 2.122L7 9.62l-4.595 4.597-2.122-2.122L4.878 7.5.282 2.904 2.404.782l4.595 4.596L11.596.782Z" fill="#69707D" fill-rule="evenodd"/></svg>
    </section>
</template>

<style scoped>
.container {
    width: 50%;
    max-width: 445px;
    position: relative;
}
.swiper {
    position: static;
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

svg path {
    fill: var(--white);
    transition: .2s;
}
svg:hover path {
    fill: var(--orange);
}
.icon-close {
    position: absolute;
    top: -2.5rem;
    right: 0;
    cursor: pointer;
    transform: scale(1.5);
}

/* Media Query */
@media screen and (max-width: 880px) {
    .container {
        width: 100%;
        max-width: 500px;
        margin-top: 2rem;
    }
    .swiper:nth-child(2) .swiper-slide-thumb-active::after {
        content: "";
        width: 88px;
        height: 88px;
        border-radius: .5rem;
    }

}

@media screen and (max-width: 680px) {
    .container {
        display: none;
    }
}
</style>