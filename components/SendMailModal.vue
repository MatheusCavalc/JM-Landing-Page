<script setup>
import MailIcon from '~/assets/icons/MailIcon.vue';
import CloseIcon from '~/assets/icons/CloseIcon.vue';
import { ref } from 'vue'
import { TransitionRoot, TransitionChild, Dialog, DialogPanel, DialogTitle, } from '@headlessui/vue'

const isOpen = ref(false)
const subject = ref('')
const body = ref('')

function closeModal() {
    isOpen.value = false
}
function openModal() {
    isOpen.value = true
}

const sendEmail = () => {
    const mailtoLink = `mailto:jm@jmdistribuidora.com.br?subject=${subject.value}&body=${body.value}`;

    window.location.href = mailtoLink;
};
</script>

<template>
    <div
        class="z-10 p-2 fixed animate-bounce bottom-4 border border-[#E40001] right-4 rounded-full bg-[#FAF900] hover:bg-yellow-400 transition-all duration-300 ease-in-out">
        <p class="cursor-pointer" @click="openModal">
            <MailIcon class="size-10" />
        </p>
    </div>

    <TransitionRoot appear :show="isOpen" as="template">
        <Dialog as="div" @close="closeModal" class="relative z-10">
            <TransitionChild as="template" enter="duration-300 ease-out" enter-from="opacity-0" enter-to="opacity-100"
                leave="duration-200 ease-in" leave-from="opacity-100" leave-to="opacity-0">
                <div class="fixed inset-0 bg-black/25" />
            </TransitionChild>

            <div class="fixed inset-0 overflow-y-auto">
                <div class="flex min-h-full items-center justify-center p-4 text-center">
                    <TransitionChild as="template" enter="duration-300 ease-out" enter-from="opacity-0 scale-95"
                        enter-to="opacity-100 scale-100" leave="duration-200 ease-in" leave-from="opacity-100 scale-100"
                        leave-to="opacity-0 scale-95">
                        <DialogPanel
                            class="w-full max-w-2xl transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all">

                            <div class="flex justify-end">
                                <CloseIcon class="h-6" @click="closeModal" />
                            </div>

                            <DialogTitle as="h3" class="text-xl font-medium leading-6 text-gray-900">
                                Envie um email para a gente
                            </DialogTitle>

                            <form v-on:submit="sendEmail">
                                <div class="mt-4">
                                    <div class="mb-6 mt-2">
                                        <label for="default-input" class="block mb-2 text-sm text-gray-900">
                                            Assunto
                                        </label>
                                        <input type="text" required v-model="subject"
                                            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg block w-full p-2.5">
                                    </div>

                                    <div class="mb-6 mt-2">
                                        <label for="message" class="block mb-2 text-sm text-gray-900">
                                            Escrever e-mail</label>
                                        <textarea required rows="4" v-model="body"
                                            class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300"></textarea>
                                    </div>
                                </div>

                                <div class="mt-4">
                                    <button type="submit"
                                        class="inline-flex justify-center rounded-md border border-transparent bg-[#E40001] px-4 py-2 text-sm font-medium text-white">
                                        Enviar
                                    </button>
                                </div>
                            </form>

                        </DialogPanel>
                    </TransitionChild>
                </div>
            </div>
        </Dialog>
    </TransitionRoot>


</template>