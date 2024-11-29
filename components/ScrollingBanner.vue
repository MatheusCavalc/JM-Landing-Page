<template>
    <div class="my-10" id="Produtos">
        <div class="mx-4">
            <p class="font-bold text-2xl text-center lg:text-3xl">Trabalhamos com marcas de alta qualidade</p>
        </div>

        <div class="tech-slideshow w-full my-5">
            <div class="mover-1 flex items-center gap-16 lg:gap-32">
                <img src="../assets/images/Ruffles-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Fandangos-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Lays-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Cheetos-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Doritos-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Elma-Chips-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Toddy-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Kero-Coco-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/quaker-logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Ruffles-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Fandangos-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Lays-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Cheetos-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Doritos-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Elma-Chips-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Toddy-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/Kero-Coco-Logo.png" class="h-24 object-cover">
                    
                <img src="../assets/images/quaker-logo.png" class="h-24 object-cover">
            </div>

        </div>
    </div>
</template>

<style>
.tech-slideshow {
  height: 150px;
  overflow: hidden;
  transform: translate3d(0, 0, 0);
}

.tech-slideshow > div {
  height: 150px;
  width: 2526px;
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  transform: translate3d(0, 0, 0);
}
.tech-slideshow .mover-1 {
  animation: moveSlideshow 15s linear infinite;
}
.tech-slideshow .mover-2 {
  opacity: 0;
  transition: opacity 0.5s ease-out;
  background-position: 0 -200px;
  animation: moveSlideshow 15s linear infinite;
  transition-delay: 15s;
}
.tech-slideshow:hover .mover-2 {
  opacity: 1;
}

@keyframes moveSlideshow {
  100% { 
    transform: translateX(-66.6666%);  
  }
}
</style>