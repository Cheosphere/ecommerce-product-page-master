<script setup>
import { ref } from 'vue'
import MenuMobile from '../components/MenuMobile.vue'

const props = defineProps(['counter','total'])

const cartDetail = ref(null)
const iconCart = ref(null)

const showDetail = () => {
    cartDetail.value.classList.toggle('show-detail')
    iconCart.value.classList.toggle('color-cart')
}

const emit = defineEmits(['countReset'])

const reset = () => {
    emit('countReset', props.total)
}

</script>

<template>
    <header class="header">
        <div class="menu-mobile">
            <MenuMobile />
        </div>
        <figure class="header-logo">
            <img src="../assets/images/logo.svg" alt="logo image">
        </figure>
        <nav class="header-nav">
            <ul class="header-nav-menu">
                <li class="header-nav-menu-item"><a class="hover_link" href="javascript:;">Collections</a></li>
                <li class="header-nav-menu-item"><a class="hover_link" href="javascript:;">Men</a></li>
                <li class="header-nav-menu-item"><a class="hover_link" href="javascript:;">Women</a></li>
                <li class="header-nav-menu-item"><a class="hover_link" href="javascript:;">About</a></li>
                <li class="header-nav-menu-item"><a class="hover_link" href="javascript:;">Contact</a></li>
            </ul>
            <article class="header-nav-user">
                <figure class="header-nav-user-cart" @click="showDetail">
                    <span v-if="props.counter != 0">{{ props.counter }}</span>
                    <svg width="22" height="20" xmlns="http://www.w3.org/2000/svg"><path ref="iconCart" d="M20.925 3.641H3.863L3.61.816A.896.896 0 0 0 2.717 0H.897a.896.896 0 1 0 0 1.792h1l1.031 11.483c.073.828.52 1.726 1.291 2.336C2.83 17.385 4.099 20 6.359 20c1.875 0 3.197-1.87 2.554-3.642h4.905c-.642 1.77.677 3.642 2.555 3.642a2.72 2.72 0 0 0 2.717-2.717 2.72 2.72 0 0 0-2.717-2.717H6.365c-.681 0-1.274-.41-1.53-1.009l14.321-.842a.896.896 0 0 0 .817-.677l1.821-7.283a.897.897 0 0 0-.87-1.114ZM6.358 18.208a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm10.015 0a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm2.021-7.243-13.8.81-.57-6.341h15.753l-1.383 5.53Z" fill="#69707D" fill-rule="nonzero"/></svg>
                </figure>
                <div class="cart-detail" ref="cartDetail">
                    <div class="cart-detail-header">
                        <h3>Cart</h3>
                    </div>
                    <div class="cart-detail-info">
                        <p class="cart-detail-info-empty" v-if="props.counter === 0 || props.counter === ''">Your cart is empty</p>
                        <div class="cart-detail-info-summary" v-if="props.counter != 0">
                            <figure>
                                <img class="cart-detail-info-summary-img" src="../assets/images/image-product-1-thumbnail.jpg" alt="image product">
                            </figure>
                            <div>
                                <div ref="details">
                                    <p>Fall Limited Edition Sneakers</p>
                                    <span>$125.00 &nbsp;x &nbsp;</span>
                                    <span>{{ props.counter }}&nbsp;</span>
                                    <span> ${{ props.total }}.00</span>
                                </div>
                            </div>
                            <svg @click="reset" class="trash-icon" width="14" height="16" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M0 2.625V1.75C0 1.334.334 1 .75 1h3.5l.294-.584A.741.741 0 0 1 5.213 0h3.571a.75.75 0 0 1 .672.416L9.75 1h3.5c.416 0 .75.334.75.75v.875a.376.376 0 0 1-.375.375H.375A.376.376 0 0 1 0 2.625Zm13 1.75V14.5a1.5 1.5 0 0 1-1.5 1.5h-9A1.5 1.5 0 0 1 1 14.5V4.375C1 4.169 1.169 4 1.375 4h11.25c.206 0 .375.169.375.375ZM4.5 6.5c0-.275-.225-.5-.5-.5s-.5.225-.5.5v7c0 .275.225.5.5.5s.5-.225.5-.5v-7Zm3 0c0-.275-.225-.5-.5-.5s-.5.225-.5.5v7c0 .275.225.5.5.5s.5-.225.5-.5v-7Zm3 0c0-.275-.225-.5-.5-.5s-.5.225-.5.5v7c0 .275.225.5.5.5s.5-.225.5-.5v-7Z" id="a"/></defs><use fill="#C3CAD9" fill-rule="nonzero" xlink:href="#a"/></svg>
                            <button @click="showDetail" class="checkout-btn">Checkout</button>
                        </div>
                    </div>
                </div>
                <figure class="header-nav-user-avatar">
                    <img src="../assets/images/image-avatar.png" alt="avatar photo">
                </figure>
            </article>
        </nav>
    </header>
</template>

<style scoped>
.header {
    width: 1110px;
    height: 113px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid rgb(182, 188, 200, .35);
    transition: .2s;
    z-index: 10;
}
.menu-mobile {
    display: none;
}
.header-logo {
    z-index: -5;
}
.header-nav {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.header-nav-menu {
    margin-left: 3.5rem;
    margin-bottom: .4rem;
    display: flex;
}
.header-nav-menu-item {
    margin-right: 2.05rem;
    list-style: none;
    position: relative;
}

a {
    font-size: .93rem;
    font-weight: 300;
    letter-spacing: .01rem;
    text-decoration: none;
    color: var(--dark-grayish-blue);
}

.header-nav-menu-item:hover a {
    font-weight: 400;
    color: var(--very-dark-blue);
}
.hover_link::after {
    width: 100%;
    height: 5px;
    position: absolute;
    top: 4.07rem;
    left: 0px;
    bottom: -4px;
    content: "";
    transform: scaleX(0);
    transition: transform 0.3s ease 0s;
    background-color: var(--orange);
}
.hover_link:hover::after {
    transform: scaleX(1);
}
.header-nav-user {
    display: flex;
    align-items: center;
    position: relative;
}
.header-nav-user-cart {
    cursor: pointer;
    position: relative;
    z-index: 10;
}
.header-nav-user-cart span {
    width: 20px;
    height: 14px;
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    right: 2.5rem;
    top: -.3rem;
    font-size: .6rem;
    font-weight: 700;
    border-radius: 15px;
    color: var(--white);
    background-color: var(--orange);
}
.color-cart {
    fill: #000;
}
.header-nav-user-cart svg {
    margin:.2rem 2.85rem 0 0;
}
.header-nav-user-cart svg path {
    transition: .2s;
}
.header-nav-user-cart:hover svg path {
    fill: black;
}
.header-nav-user-avatar {
    width: 50px;
    height: 50px;
    margin-bottom: .2rem;
    position: relative;
    cursor: pointer;
    transition: .3s;
}

.header-nav-user-avatar img {
    width: 100%;
    border-radius: 50px;
    outline: 2px solid rgb(255, 125, 26, 0);
    transition: .2s;
}

.header-nav-user-avatar:hover img {
    outline: 2px solid rgb(255, 125, 26, 1);
}
.cart-detail {
    width: 360px;
    height: 256px;
    display: none;
    position: absolute;
    top: 4.1rem;
    right: -4.8rem;
    background-color: var(--white);
    border-radius: .7rem;
    box-shadow: 0px 28px 38px -10px rgba(0,0,0,.25);
    transition: .2s;
    z-index: -1;
}
.show-detail {
    display: block;
}
.cart-detail-header {
    width: 100%;
    height: 68px;
    padding: 1.5rem;
    border-bottom: 1px solid rgba(211, 211, 211, 0.5);
}
.cart-detail-header h3 {
    font-size: 1rem;
    color: var(--very-dark-blue);
}
.cart-detail-info {
    width: 312px;
    height: 188px;
    margin: 1.5rem auto;
}
.cart-detail-info p {
    align-self: center;
    text-align: center;
    font-weight: 600;
    color: var(--dark-grayish-blue);
}
.cart-detail-info .cart-detail-info-empty {
    line-height: 128px;
}
.cart-detail-info-summary {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
}
.cart-detail-info-summary div div p {
    margin-top: -.2rem;
    margin-bottom: .4rem;
}
.cart-detail-info-summary p,
.cart-detail-info-summary span {
    color: var(--dark-grayish-blue);
    font-weight: 300;
}
.cart-detail-info-summary span:nth-child(4) {
    color: var(--very-dark-grayish-blue);
    font-weight: 700;
}
.trash-icon {
    cursor: pointer;
}
.trash-icon use {
    transition: .2s;
}
.trash-icon:hover use {
    fill: var(--orange);
}
.cart-detail-info-summary-img {
    width: 50px;
    height: 50px;
    border-radius: 5px;
}
.checkout-btn {
    width: 100%;
    height: 56px;
    margin-top: 1.3rem;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
    font-family: 'Kumbh Sans', sans-serif;
    border-radius: .6rem;
    border: none;
    background-color: var(--orange);
    color: var(--white);
    cursor: pointer;
    transition: .2s;
}

.checkout-btn:hover {
    background-color: hsl(26, 100%, 55%, .5);
}

/* Media Query */
@media screen and (max-width: 1280px) {
    .header {
        padding: 0 5rem;
    }
}

@media screen and (max-width: 880px) {
    .header {
        width: 100%;
        padding: 0 2rem;
    }
    .menu-mobile {
        display: block;
    }
    .header-nav-menu {
        display: none;
    }
    .header-nav-user {
        margin-left: auto;
    }
    .cart-detail {
        top: 4.5rem;
        right: -1rem;
    }
}

@media screen and (max-width: 680px) {
    .header {
        height: 80px;
    }
    .header-nav-user-cart svg {
        margin: .2rem 1.5rem 0 0;
    }
    .header-nav-user-cart span {
        right: 1rem;
        top: -.1rem;
    }
    .header-nav-user-avatar {
        width: 30px;
        height: 30px;
    }
    
}

@media screen and (max-width: 520px) {
    .header {
        padding: 0 1rem;
    }
    .header-nav-user {
        position: static;
    }
    .cart-detail {
        width: 95%;
        padding: 0 1rem 1rem 1rem;
        top: 6rem;
        left: 50%;
        transform: translate(-50%);
    }
    .cart-detail-info {
        width: 100%;
    }
}
</style>