<script setup>
import { ref, onMounted, onBeforeUnmount, computed } from 'vue';
import JMLogo from '~/assets/icons/JMLogo.vue';
import MailIcon from '~/assets/icons/MailIcon.vue';

const menu = ref(false)

const isHidden = ref(false);
let lastScrollTop = 0;

const isNavbarOpaque = ref(false);

const handleScroll = () => {
    const scrollThreshold = 80;
    isNavbarOpaque.value = window.scrollY > scrollThreshold;

    const currentScrollTop = window.pageYOffset || document.documentElement.scrollTop;

    if (currentScrollTop > lastScrollTop) {
        // Scroll para baixo
        isHidden.value = true;
    } else {
        // Scroll para cima
        isHidden.value = false;
    }

    lastScrollTop = currentScrollTop <= 0 ? 0 : currentScrollTop;
};

const currentMonth = new Date().getMonth();
const isJune = computed(() => currentMonth === 5);
const isDecember = computed(() => currentMonth === 11);

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
});

onBeforeUnmount(() => {
    window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
    <nav :class="{ 'bg-[#FAF900] text-black': isNavbarOpaque || menu, 'text-[#FAF900]': isHidden, 'text-[#FAF900]': !isHidden }"
        class="fixed top-0 z-30 w-full transition duration-300 ease-in-out">
        <div class="flex flex-wrap items-center justify-between max-w-screen-2xl px-1 lg:px-4 py-3 lg:py-0 mx-auto">
            <NuxtLink to="/" class="flex items-center lg:gap-1">

                <JMLogo v-if="!isJune && !isDecember" class="w-12 lg:w-16"
                    :class="{ 'fill-[#FAF900]': !isNavbarOpaque, 'fill-black': isNavbarOpaque }" />

                <img v-else-if="isJune" src="../assets/images/JM-Logo-Festa-Junina.png"
                    class="w-12 lg:w-20 mb-2 ml-1 lg:ml-0" />

                <img v-else-if="isDecember" src="../assets/images/JM-Logo-Natal.png"
                    class="w-12 lg:w-20 mb-2 ml-1 lg:ml-0" />

                <span class="self-center text-xl font-semibold lg:text-2xl italic whitespace-nowrap"
                    :class="{ 'text-black': isNavbarOpaque }">
                    Distribuidora</span>
            </NuxtLink>

            <!--
            <div class="lg:order-3">
                <a href="https://wa.me/+55859" target="_blank">
                    <Button>Compre Agora</Button>
                </a>
            </div>
            -->

            <div class="flex lg:order-2 stroke-[#FAF900] transition duration-300 ease-in-out"
                :class="{ 'stroke-black': isNavbarOpaque || menu }">
                <button @click="menu = !menu" :class="{ 'opened': menu }"
                    class="inline-flex items-center justify-center w-10 h-10 p-1 text-sm rounded-lg lg:hidden">
                    <svg width="100" height="100" viewBox="0 0 100 100">
                        <path class="line line1"
                            d="M 20,29.000046 H 80.000231 C 80.000231,29.000046 94.498839,28.817352 94.532987,66.711331 94.543142,77.980673 90.966081,81.670246 85.259173,81.668997 79.552261,81.667751 75.000211,74.999942 75.000211,74.999942 L 25.000021,25.000058" />
                        <path class="line line2" d="M 20,50 H 80" />
                        <path class="line line3"
                            d="M 20,70.999954 H 80.000231 C 80.000231,70.999954 94.498839,71.182648 94.532987,33.288669 94.543142,22.019327 90.966081,18.329754 85.259173,18.331003 79.552261,18.332249 75.000211,25.000058 75.000211,25.000058 L 25.000021,74.999942" />
                    </svg>
                </button>
            </div>

            <div :class="{ 'lg:block': menu, 'hidden lg:block': !menu }" class="w-full lg:w-auto lg:order-1"
                id="navbar-default">
                <ul :class="{ 'bg-[#FAF900]': isNavbarOpaque, '': !isNavbarOpaque, 'text-black': isNavbarOpaque }"
                    class="flex flex-col p-4 mt-4 font-normal border border-gray-100 rounded-lg lg:p-0 lg:flex-row lg:space-x-8 lg:mt-0 lg:border-0 lg:bg-transparent transition duration-300 ease-in-out lg:transition-none">
                    <a @click="menu = false" href="#Sobre">
                        <li>
                            <button class="block py-2 pl-3 pr-4 rounded lg:border-0 lg:py-5">
                                Sobre
                            </button>
                        </li>
                    </a>
                    <a @click="menu = false" href="#Produtos">
                        <li>
                            <button class="block py-2 pl-3 pr-4 rounded lg:border-0 lg:py-5">
                                Produtos
                            </button>
                        </li>
                    </a>
                    <a @click="menu = false" href="#Parceiros">
                        <li>
                            <button class="block py-2 pl-3 pr-4 rounded lg:border-0 lg:py-5">
                                Parceiros
                            </button>
                        </li>
                    </a>
                    <a @click="menu = false" href="#Diferenciais">
                        <li>
                            <button class="block py-2 pl-3 pr-4 rounded lg:border-0 lg:py-5">
                                Diferenciais
                            </button>
                        </li>
                    </a>
                    <a @click="menu = false" href="#Contato">
                        <li>
                            <button class="block py-2 pl-3 pr-4 rounded lg:border-0 lg:py-5">
                                Contato
                            </button>
                        </li>
                    </a>
                    <a @click="menu = false" href="#TrabalheConosco">
                        <li>
                            <button class="block py-2 pl-3 pr-4 rounded lg:border-0 lg:py-5">
                                Trabalhe Conosco
                            </button>
                        </li>
                    </a>
                </ul>
            </div>
        </div>
    </nav>

    <div class="relative">
        <SendMailModal />

        <slot />
    </div>

    <footer class="bg-[#E40001]">
        <div class="w-full max-w-screen-xl mx-auto p-4 md:py-8">
            <div class="space-y-5 sm:flex sm:items-center sm:justify-between">
                <NuxtLink to="/" class="flex items-center lg:gap-1">
                    <JMLogo class="w-12 lg:w-16 fill-[#FAF900]" />
                    <span
                        class="self-center text-white text-xl font-semibold lg:text-2xl italic whitespace-nowrap px-3 lg:px-0"
                        :class="{ 'text-black': isNavbarOpaque }">
                        Distribuidora</span>
                </NuxtLink>
                <ul class="grid grid-cols-2 gap-5 lg:gap-x-5 items-center mb-6 text-white font-medium sm:mb-0">
                    <li>
                        <a href="#Sobre" class="hover:underline me-4 md:me-6">Sobre</a>
                    </li>
                    <li>
                        <a href="#Produtos" class="hover:underline me-4 md:me-6">Produtos</a>
                    </li>
                    <li>
                        <a href="#Parceiros" class="hover:underline me-4 md:me-6">Parceiros</a>
                    </li>
                    <li>
                        <a href="#Diferenciais" class="hover:underline me-4 md:me-6">Diferenciais</a>
                    </li>
                    <li>
                        <a href="#Contato" class="hover:underline me-4 md:me-6">Contato</a>
                    </li>
                    <li>
                        <a href="#TrabalheConosco" class="hover:underline me-4 md:me-6">Trabalhe Conosco</a>
                    </li>
                </ul>
            </div>
            <hr class="my-6 border-gray-200 sm:mx-auto lg:my-8" />
            <span class="block text-sm text-gray-800 sm:text-center">© 2024 <a href="/" class="hover:underline">JM
                    Distribuidora™</a>. All Rights Reserved.</span>
        </div>
    </footer>
</template>

<style>
.menu {
    background-color: transparent;
    border: none;
    cursor: pointer;
    display: flex;
    padding: 0;
}

.line {
    fill: none;
    stroke-width: 7;
    transition: stroke-dasharray 500ms cubic-bezier(0.4, 0, 0.2, 1),
        stroke-dashoffset 500ms cubic-bezier(0.4, 0, 0.2, 1);
}

.line1 {
    stroke-dasharray: 60 207;
    stroke-width: 7;
}

.line2 {
    stroke-dasharray: 60 60;
    stroke-width: 7;
}

.line3 {
    stroke-dasharray: 60 207;
    stroke-width: 7;
}

.opened .line1 {
    stroke-dasharray: 90 207;
    stroke-dashoffset: -134;
    stroke-width: 6;
}

.opened .line2 {
    stroke-dasharray: 1 60;
    stroke-dashoffset: -30;
    stroke-width: 6;
}

.opened .line3 {
    stroke-dasharray: 90 207;
    stroke-dashoffset: -134;
    stroke-width: 6;
}

.v-enter-active,
.v-leave-active {
    transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
    opacity: 0;
}
</style>