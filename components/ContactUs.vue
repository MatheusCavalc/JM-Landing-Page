<script setup>
import { ref } from 'vue'

const nome = ref("")
const estabelecimento = ref("")
const endereço = ref("")
const cidade = ref("")
const bairro = ref("")
const telefone = ref("")
const assunto = ref("")

const sendEmail = () => {
    const subject = encodeURIComponent('Contato via Landing Page');
    const body = encodeURIComponent(`Nome: ${nome}\n` + `Estabelecimento: ${estabelecimento}\n` + `Endereço: ${endereço}\n` + `Cidade: ${cidade}\n` + `Bairro: ${bairro}\n` + `Telefone: ${telefone}\n\n` + `${assunto}`);
    const mailtoLink = `mailto:jm@jmdistribuidora.com.br?subject=${subject}&body=${body}`;

    //console.log(body, nome)
    window.location.href = mailtoLink;
};
</script>

<template>
    <div id="Contato" class="py-20 px-4 lg:px-28">
        <div>
            <p class="text-2xl lg:text-3xl font-black text-center">Entre em contato com a gente</p>
        </div>

        <form @submit.prevent="sendEmail" class="mx-auto my-5 p-5 rounded-lg shadow-2xl">

            <div class="flex flex-col lg:flex-row justify-center gap-1 lg:gap-5">
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="nome"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-[#E40001] peer" />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto peer-focus:text-[#E40001] peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">
                        Nome</label>
                </div>
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="estabelecimento"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-[#E40001] peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 peer-focus:text-[#E40001] peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">
                        Estabelecimento</label>
                </div>
            </div>

            <div class="flex flex-col lg:flex-row justify-center gap-1 lg:gap-5">
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="endereço"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-[#E40001] peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto peer-focus:text-[#E40001] peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">Endereço</label>
                </div>
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="cidade"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-[#E40001] peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 peer-focus:text-[#E40001] peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">Cidade</label>
                </div>
            </div>

            <div class="flex flex-col lg:flex-row justify-center gap-1 lg:gap-5">
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="bairro"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-[#E40001] peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto peer-focus:text-[#E40001] peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">
                        Bairro</label>
                </div>
                <div class="relative z-0 w-full mb-5 group">
                    <input type="number" v-model="telefone"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-[#E40001] peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 peer-focus:text-[#E40001] peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">Telefone</label>
                </div>
            </div>

            <div>
                <label for="message" class="block mb-2 text-sm text-gray-500">Assunto</label>
                <textarea id="message" rows="4" v-model="assunto"
                    class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-[#E40001] focus:border-[#E40001]"
                    placeholder=""></textarea>
            </div>

            <div class="flex justify-end mt-5">
                <button type="submit"
                    class="bg-[#FAF900] hover:bg-yellow-400 focus:outline-none font-medium rounded-full text-sm w-full sm:w-auto px-5 py-2.5 text-center">Entrar
                    em Contato</button>
            </div>
        </form>
    </div>
</template>