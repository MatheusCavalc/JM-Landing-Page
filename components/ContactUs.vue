<script setup>
const nome = ''
const estabelecimento = ""
const endereço = ""
const cidade = ""
const bairro = ""
const telefone = ""
const produtos = ""

const sendEmail = () => {
    const subject = encodeURIComponent('Contato via Landing Page');
    const body = encodeURIComponent(`Nome: ${nome}\n` + `Estabelecimento: ${estabelecimento}\n` + `Endereço: ${endereço}\n` + `Cidade: ${cidade}\n` + `Bairro: ${bairro}\n` + `Telefone: ${telefone}\n` + `Produtos de Interesse: ${produtos}\n\n` + `Prezado(a) ${nome},\n\n` + `Gostaríamos de expressar nosso interesse em nos tornar clientes da JM Distribuidora. Somos um estabelecimento localizado em ${address}, no bairro ${neighborhood}, na cidade de ${city}. Nosso telefone para contato é ${phone}.\n\n` + `Estamos interessados em adquirir os produtos da Pepsico distribuídos pela JM Distribuidora, pois acreditamos que a qualidade e a variedade dos produtos oferecidos atenderão perfeitamente às necessidades dos nossos clientes. Acreditamos que uma parceria com a JM Distribuidora será benéfica para ambos os lados, permitindo-nos oferecer produtos de alta qualidade e fortalecer nossa posição no mercado.\n\n` + `Aguardamos ansiosamente a oportunidade de discutir essa parceria e estamos à disposição para quaisquer informações adicionais que possam ser necessárias.\n\n` + `Atenciosamente,\n` + `${nome}`);
    const mailtoLink = `mailto:jm@jmdistribuidora.com.br?subject=${subject}&body=${body}`;
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
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">
                        Nome</label>
                </div>
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="estabelecimento"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">
                        Estabelecimento</label>
                </div>
            </div>

            <div class="flex flex-col lg:flex-row justify-center gap-1 lg:gap-5">
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="endereço"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">Endereço</label>
                </div>
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="cidade"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">Cidade</label>
                </div>
            </div>

            <div class="flex flex-col lg:flex-row justify-center gap-1 lg:gap-5">
                <div class="relative z-0 w-full mb-5 group">
                    <input type="text" v-model="bairro"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">
                        Bairro</label>
                </div>
                <div class="relative z-0 w-full mb-5 group">
                    <input type="number" v-model="telefone"
                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer"
                        placeholder=" " required />
                    <label
                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:start-0 rtl:peer-focus:translate-x-1/4 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6">Telefone</label>
                </div>
            </div>

            <div>
                <label for="message" class="block mb-2 text-sm text-gray-500">Assunto</label>
                <textarea id="message" rows="4" v-model="produtos"
                    class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500"
                    placeholder=""></textarea>
            </div>

            <div class="flex justify-end mt-5">
                <a :href="`mailto:jm@jmdistribuidora.com.br?subject=${subject}&body=${body}`" target="_blank">
                    <button
                        class="bg-[#FAF900] hover:bg-yellow-400 focus:outline-none font-medium rounded-full text-sm w-full sm:w-auto px-5 py-2.5 text-center">Entrar
                        em Contato</button>
                </a>
            </div>
        </form>
    </div>
</template>