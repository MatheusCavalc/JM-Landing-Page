<script setup>
import { onMounted } from 'vue';

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
    <div id="Sobre" class="py-20 px-4 lg:px-20 space-y-5">
        <div data-animation="left">
            <p class="text-2xl lg:text-3xl font-black mb-4">Sobre nós</p>

            <div class="lg:text-lg space-y-3">
                <p>
                    Fundada em 1999, a JM Distribuidora tem se dedicado a fornecer produtos de alta
                    qualidade para diversas cidades do interior do Ceará. Como distribuidora oficial
                    dos produtos Pepsico, temos o compromisso de levar até você as melhores marcas e
                    produtos que fazem parte do seu dia a dia.
                </p>

                <p>
                    Ao longo dos anos, construímos uma sólida reputação baseada na confiança, eficiência
                    e excelência no atendimento. Nossa missão é garantir que nossos clientes recebam
                    produtos frescos e de qualidade, sempre com um serviço ágil e personalizado.
                </p>

                <p>
                    A JM Distribuidora trabalha com pré-venda e pronta entrega, oferecendo flexibilidade
                    e conveniência para atender às necessidades dos nossos clientes. Estamos presentes
                    em várias cidades do interior do Ceará, levando a qualidade Pepsico para mais perto
                    de você. Com uma equipe dedicada e uma logística eficiente, a JM Distribuidora
                    se orgulha de ser uma referência no setor de distribuição de alimentos na região.
                </p>
            </div>
        </div>
    </div>
</template>