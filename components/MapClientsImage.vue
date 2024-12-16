<template>
  <div class="image flex justify-center h-80 sm:h-[450px] lg:h-[800px] overflow-hidden">
    <img alt="Mapa da região atendida e principais parceiros" src="../assets/images/Região-Atendida-Limpo-Clientes.png"
      class="h-80 sm:h-[450px] lg:h-[800px] object-cover" srcset="">
  </div>
</template>

<script setup>
import { onMounted } from 'vue';

onMounted(() => {
  document.querySelectorAll('.image').forEach(elem => {
    let x, y, width, height;
    elem.onmouseenter = () => {
      const size = elem.getBoundingClientRect();

      x = size.x;
      y = size.y;
      width = size.width;
      height = size.height;
    };

    elem.onmousemove = e => {
      const horizontal = (e.clientX - x) / width * 100;
      const vertical = (e.clientY - y) / height * 100;

      elem.style.setProperty('--x', horizontal + '%');
      elem.style.setProperty('--y', vertical + '%');
    };
  });
}); 
</script>

<style scoped>
.image img {
  -o-object-fit: cover;
  object-fit: cover;
  transform: scale(var(--zoom, 1));
  transform-origin: var(--x) var(--y);
  transition: transform 0.1 ease;
}

.image:hover {
  --zoom: 1.4;
}

@media (max-width: 640px) {
  .image img {
    transform: scale(var(--zoom, 1));
    transition: transform 0.1s ease;
  }

  .image:hover {
    --zoom: 2.2;
    /* Reduz o nível de zoom em telas menores */
  }
}
</style>