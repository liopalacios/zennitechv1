<template>
  <div>
    <section class="section" ref="section1">
        <div class="background-image"  :class="{ 'show-image': showImage }">

        </div>
        <div class="animated-rectangle">
            <div class="content-asesoria">
                <p style="font-size: 3.2rem;font-family: sans-serif;" class="zoom-text">
                    Consultoria en tecnologías emergentes</p>
            </div>
        </div>
    </section>
    <section class="section flex content-center">
      <div  class="md:w-4/6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 
                  dark:border-gray-700 m-auto">   
        <p class="pt-4 text-2xl font-bold">Asesoria Tecnológica</p>
        <hr class="hr-text" data-content="">
        <div class="text-md flex justify-between px-4 my-2">
          <span class="font-bold">Soluciones Informáticas de alta calidad</span>
          <span class="font-bold"></span>
        </div>
        <p class="hidden md:block px-4 my-4 text-sm text-left">En un mundo en constante evolución tecnológica, mantenerse al día con las últimas innovaciones es crucial para cualquier empresa que desee conservar su competitividad. Nuestro equipo de expertos en tecnologías emergentes se dedica a brindar asesoramiento personalizado, ayudando a tu organización a identificar, evaluar e implementar las soluciones más avanzadas del mercado. Desde inteligencia artificial y blockchain hasta la Internet de las Cosas (IoT) y la realidad aumentada, te guiamos en la adopción de estas tecnologías disruptivas para optimizar tus operaciones, mejorar la experiencia del cliente y abrir nuevas oportunidades de negocio. Con nuestra asesoría, tu empresa estará a la vanguardia de la innovación tecnológica. </p>
        <p class="flex text-md px-4 my-2">
          Productos: Marketing, Ventas, Digitalización, Banca y Seguros
          <span class="font-bold px-2">|</span>
          Tecnologias: Java, Python, Android, 
        </p>        
        <div class="text-xs">
          <button type="button" class="border border-gray-400 text-gray-400 rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-gray-900 focus:outline-none focus:shadow-outline">Postgres</button>
          <button type="button" class="border border-gray-400 text-gray-400 rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-gray-900 focus:outline-none focus:shadow-outline">SQL</button>
          <button type="button" class="border border-gray-400 text-gray-400 rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-gray-900 focus:outline-none focus:shadow-outline">Oracle</button>
        </div>      
      </div>
    </section>
  </div>
</template>

<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'
const showImage = ref(false);
onMounted(() => {
    // Mostrar gradualmente la imagen después de que el componente se monta
    setTimeout(() => {
      showImage.value = true;
    }, 400); // Retraso pequeño para que se vea la transición
  });
</script>

<style>
 

</style>