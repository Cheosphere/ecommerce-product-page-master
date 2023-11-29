<script setup>
import { ref } from 'vue'

const count = ref(0)

const countAdd = () => {
    count.value++
}

const countSub = () => {
    if (count.value > 0) {
        count.value--
    }
}

const emit = defineEmits(['countRegistered'])

const sendCount = () => {
    emit('countRegistered', count.value)
}

</script>

<template>
    <section class="container">
        <h4 class="content-name">SNEAKER COMPANY</h4>
        <h1 class="content-title">Fall Limited Edition Sneakers</h1>
        <p class="content-text">
            These low-profile sneakers are your perfect casual wear companion. Featuring a 
            durable rubber outer sole, they’ll withstand everything the weather can offer.
        </p>
        <article class="content-price">
            <h3 class="content-price-sale">$125.00</h3>
            <span class="content-price-off"><p>50%</p></span>
            <span class="content-price-normal">$250.00</span>
            <hr>
        </article>
        <article class="digits-container" >
            <div class="digits">
                <button class="digits-minus" @click="countSub">
                    <svg width="12" height="4" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M11.357 3.332A.641.641 0 0 0 12 2.69V.643A.641.641 0 0 0 11.357 0H.643A.641.641 0 0 0 0 .643v2.046c0 .357.287.643.643.643h10.714Z" id="a"/></defs><use fill="#FF7E1B" fill-rule="nonzero" xlink:href="#a"/></svg>
                </button>
                <h5 class="digits-count">{{ count }}</h5>
                <button class="digits-add" @click="countAdd">
                    <svg width="12" height="12" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M12 7.023V4.977a.641.641 0 0 0-.643-.643h-3.69V.643A.641.641 0 0 0 7.022 0H4.977a.641.641 0 0 0-.643.643v3.69H.643A.641.641 0 0 0 0 4.978v2.046c0 .356.287.643.643.643h3.69v3.691c0 .356.288.643.644.643h2.046a.641.641 0 0 0 .643-.643v-3.69h3.691A.641.641 0 0 0 12 7.022Z" id="b"/></defs><use fill="#FF7E1B" fill-rule="nonzero" xlink:href="#b"/></svg>
                </button>
            </div>
            <button class="cart-btn" @click="sendCount">
                <svg width="22" height="20" xmlns="http://www.w3.org/2000/svg"><path d="M20.925 3.641H3.863L3.61.816A.896.896 0 0 0 2.717 0H.897a.896.896 0 1 0 0 1.792h1l1.031 11.483c.073.828.52 1.726 1.291 2.336C2.83 17.385 4.099 20 6.359 20c1.875 0 3.197-1.87 2.554-3.642h4.905c-.642 1.77.677 3.642 2.555 3.642a2.72 2.72 0 0 0 2.717-2.717 2.72 2.72 0 0 0-2.717-2.717H6.365c-.681 0-1.274-.41-1.53-1.009l14.321-.842a.896.896 0 0 0 .817-.677l1.821-7.283a.897.897 0 0 0-.87-1.114ZM6.358 18.208a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm10.015 0a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm2.021-7.243-13.8.81-.57-6.341h15.753l-1.383 5.53Z" fill="#FFF" fill-rule="nonzero"/></svg>
                <h4>Add to cart</h4>
            </button>
        </article>
    </section>
</template>

<style scoped>
.container {
    width: 50%;
    margin-top: 9.45rem;
    padding-left: 4rem;
}
.content-name {
    font-size: .85rem;
    font-weight: 500;
    letter-spacing: .09rem;
    color: var(--orange);
}
.content-title {
    margin-top: 1.2rem;
    font-size: 2.65rem;
    line-height: 3rem;
    letter-spacing: .05rem;
    color: var(--very-dark-blue);
    transition: .2s;
}
.content-text {
    margin-top: 2.2rem;
    font-size: 1.01rem;
    font-weight: 300;
    line-height: 1.6rem;
    letter-spacing: .002rem;
    color: var(--dark-grayish-blue);
}
.content-price {
    width: 180px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    margin-top: 1.55rem;
    position: relative;
}
.content-price-sale {
    font-size: 1.75rem;
    letter-spacing: .07rem;
    color: var(--very-dark-blue);
}
.content-price-off {
    min-width: 50px;
    height: 26px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 1rem;
    border-radius: 5px;
    background-color: rgb(255, 125, 26, .15);
}
.content-price-off p {
    color: var(--orange);
    font-weight: 500;
    letter-spacing: .04rem;
}
.content-price-normal {
    margin-top: .5rem;
    font-weight: 600;
    letter-spacing: .04rem;
    text-decoration: dashed;
    color: var(--grayish-blue);
}

hr {
    width: 63px;
    height: 1px;
    position: absolute;
    bottom: .5rem;
    color: transparent;
    border-bottom: 1px solid var(--grayish-blue);
}
.digits-container {
    width: 100%;
    margin-top: 2.25rem;
    display: flex;
    align-items: center;
}
.digits {
    width: 157px;
    height: 56px;
    display: flex;
    border-radius: .7rem;
}

button {
    border: none;
    cursor: pointer;
}
.digits-minus {
    width: 52px;
    height: 56px;
    padding-right: .7rem;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 8px 0 0 8px;
    background-color: var(--light-grayish-blue);
}
.digits-count {
    width: 52px;
    height: 56px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1rem;
    background-color: var(--light-grayish-blue);
}
.digits-add {
    width: 52px;
    height: 56px;
    padding-left: .7rem;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 0 8px 8px 0;
    background-color: var(--light-grayish-blue);
}

svg use {
    transition: .2s;
}

.digits-minus:hover use,
.digits-add:hover use {
    opacity: .4;
}
.cart-btn {
    width: 272px;
    height: 56px;
    margin-left: .98rem;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Kumbh Sans', sans-serif;
    border-radius: .6rem;
    background-color: var(--orange);
    color: var(--white);
    box-shadow: 0 20px 50px -15px rgb(255, 125, 26, .5);
    transition: .2s;
}
.cart-btn h4 {
    margin-left: 1rem;
    font-size: .95rem;
    font-weight: 500;
    font-family: 'Kumbh Sans', sans-serif;
    letter-spacing: .03rem;
}

.cart-btn svg {
    transform: scale(.8);
}

.cart-btn:hover {
    background-color: hsl(26, 100%, 55%, .5);
}

/* Media Query */
@media screen and (max-width: 960px) {
    .container {
        padding-left: 2.5rem;
    }
    .content-title {
        margin-top: 1.2rem;
        font-size: 2.3rem;
        line-height: 3rem;
        letter-spacing: .05rem;
        color: var(--very-dark-blue);
    }
}

@media screen and (max-width: 880px) {
    .container {
        width: 100%;
        max-width: 550px;
        margin-top: 6rem;
        padding: 0;
    }
}

@media screen and (max-width: 680px) {
    .container {
        max-width: none;
        padding: 0 2rem;
        margin-top: 2rem;
    }
}

@media screen and (max-width: 540px) {
    .content-price {
        width: 100%;
    }
    .content-price-normal {
        margin-left: auto;
    }
    .digits-container {
        flex-direction: column;
        align-items: center;
    }
    .digits {
        width: 100%;
        height: 56px;
        display: flex;
        border-radius: .7rem;
    }
    .digits-minus,
    .digits-count,
    .digits-add {
        width: 100%;
    }
    .cart-btn {
        width: 100%;
        margin: 1rem 0;
    }

    hr {
        right: 0;        
        bottom: .7rem;
        color: transparent;
        border-bottom: 1px solid var(--grayish-blue);
    }
}

@media screen and (max-width: 420px) {
    .container {
        padding: 0 1rem;
    }
    .content-title {
        font-size: 2rem;
        line-height: 2.5rem;
    }
}
</style>