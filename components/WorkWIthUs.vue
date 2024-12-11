<script setup>
import { onMounted } from 'vue';

const sendEmail = () => {
    const subject = encodeURIComponent('Quero trabalhar na JM');
    const body = encodeURIComponent('Segue em anexo o curriculo em formato PDF\n\n');
    const mailtoLink = `mailto:jm@jmdistribuidora.com.br?subject=${subject}&body=${body}`;

    window.location.href = mailtoLink;
}

const debounce = (func, wait, immediate) => {
    let timeout;
    return function (...args) {
        const context = this;
        const later = function () {
            timeout = null;
            if (!immediate) func.apply(context, args);
        };
        const callNow = immediate && !timeout;
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
        if (callNow) func.apply(context, args);
    };
};

const scrollAnimation = () => {
    const target = document.querySelectorAll('[data-animation]')

    const windowTop = window.pageYOffset + ((window.innerHeight * 4) / 5);
    target.forEach(function (el) {
        let rect = el.getBoundingClientRect()
        let scrollTop = window.pageYOffset || document.documentElement.scrollTop;
        let top = rect.top + scrollTop

        if (windowTop > top) {
            el.classList.add("animate")
        }
    })
}

onMounted(() => {
    window.addEventListener('scroll', debounce(function () {
        scrollAnimation();
    }, 100));
});
</script>

<template>
    <div id="TrabalheConosco" class="bg-section bg-cover bg-center h-screen">
        <div class="bg-gradient-to-b from-[#00000081] to-[#E40001] h-full flex flex-col justify-center items-center">
            <div data-animation="left">
                <p class="text-2xl lg:text-3xl text-white font-black text-center my-5">Trabalhe com a <span
                        class="text-[#FAF900]">gente</span></p>

                <!--
        <div>
            <div class="flex items-center justify-center w-full">
                <label for="dropzone-file"
                    class="flex flex-col items-center justify-center w-full h-64 border-2 border-gray-300 border-dashed rounded-lg cursor-pointer bg-gray-50">
                    <div class="flex flex-col items-center justify-center pt-5 pb-6">
                        <svg class="w-8 h-8 mb-4 text-gray-500 dark:text-gray-400" aria-hidden="true"
                            xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 16">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M13 13h3a3 3 0 0 0 0-6h-.025A5.56 5.56 0 0 0 16 6.5 5.5 5.5 0 0 0 5.207 5.021C5.137 5.017 5.071 5 5 5a4 4 0 0 0 0 8h2.167M10 15V6m0 0L8 8m2-2 2 2" />
                        </svg>
                        <p class="mb-2 text-sm text-gray-500 dark:text-gray-400"><span class="font-semibold">Clique para
                                carregar</span> ou arrastar e soltar seu currículo
                        </p>
                        <p class="text-xs text-gray-500 dark:text-gray-400">PDF (MAX. 800x400px)</p>
                    </div>
                    <input id="dropzone-file" type="file" class="hidden" />
                </label>
            </div>

            <div class="flex justify-end mt-4">
                <button
                    class="bg-[#E40001] hover:bg-red-500 text-white focus:outline-none font-medium rounded-full text-sm w-full sm:w-auto px-5 py-2.5 text-center">Enviar</button>
            </div>
        </div>
        -->

                <div class="flex justify-center mt-2">
                    <button @click="sendEmail()"
                        class="bg-[#E40001] hover:bg-red-500 transition-all duration-300 ease-in-out text-white focus:outline-none font-medium rounded-full text-sm w-full sm:w-auto px-5 py-2.5 text-center">
                        Envie seu currículo
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.bg-section {
    background-image: url('https://lirp.cdn-website.com/2d4e486b/dms3rep/multi/opt/O+passo+a+passo+de+uma+reuni%C3%A3o+de+neg%C3%B3cios+efetiva-1920w.jpg');
}
</style>