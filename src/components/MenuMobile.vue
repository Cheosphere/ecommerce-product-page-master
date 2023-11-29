<script setup>
import { ref, watchEffect } from 'vue'

const menuMobile = ref(null)
const iconMenu = ref(null)
const darkness = ref(null)
const isMobileMenuOpen = ref(false);

const showMenu = () => {
    menuMobile.value.classList.toggle('show-menu')
    iconMenu.value.classList.toggle('close-icon')
    darkness.value.classList.toggle('show-dark')
    isMobileMenuOpen.value = !isMobileMenuOpen.value
}


// Manejar el desplazamiento al abrir/cerrar el menú móvil
watchEffect(() => {
  if (isMobileMenuOpen.value) {
    // Deshabilitar el desplazamiento del cuerpo cuando el menú móvil está abierto
    document.body.style.overflow = 'hidden';
  } else {
    // Habilitar el desplazamiento del cuerpo cuando el menú móvil está cerrado
    document.body.style.overflow = 'auto';
  }
});

</script>

<template>
    <nav class="header-mobile-nav">
        <figure @click="showMenu" class="icon-menu" ref="iconMenu"></figure>
        <ul ref="menuMobile" class="header-mobile-nav-menu">
            <li class="header-mobile-nav-menu-item"><a href="javascript:;">Collections</a></li>
            <li class="header-mobile-nav-menu-item"><a href="javascript:;">Men</a></li>
            <li class="header-mobile-nav-menu-item"><a href="javascript:;">Women</a></li>
            <li class="header-mobile-nav-menu-item"><a href="javascript:;">About</a></li>
            <li class="header-mobile-nav-menu-item"><a href="javascript:;">Contact</a></li>
        </ul>
    </nav>
    <div class="dark" ref="darkness"></div>
</template>

<style scoped>
/* .header-mobile-nav {} */
.icon-menu {
    width: 16px;
    height: 15px;
    margin-right: 1rem;
    cursor: pointer;
    background-image: url('../assets/images/icon-menu.svg');
    background-repeat: no-repeat;
    background-size: cover;
    transition: .4s;
}
.close-icon {
    background-image: url('../assets/images/icon-close.svg');
    background-size: cover;
    transform: rotate3d(0,1,0,180deg);
}
.header-mobile-nav-menu {
    width: 300px;
    height: 100vh;
    padding: 5rem 1rem;
    position: absolute;
    top: 0;
    left: -100%;
    background-color: var(--white);
    z-index: -2;
    transition: .3s;
}
.show-menu {
    left: 0;
}
.header-mobile-nav-menu-item {
    margin: 2rem 0;
    list-style: none;
}

a {
    font-weight: 700;
    color: var(--very-dark-blue);
    text-decoration: none;
}
.dark {
    width: 100vw;
    height: 100vh;
    position: absolute;
    top: 0;
    left: -100%;
    bottom: 0;
    z-index: -5;
    background-color: rgba(0, 0, 0, .6);
}
.show-dark {
    left: 0;
}

/* Media Query */
@media screen and (max-width: 420px) {
    .header-mobile-nav-menu {
        width: 220px;
    }
}

</style>