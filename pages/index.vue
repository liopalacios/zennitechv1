<template>
    <div >
        <div class="content">
        <!-- Sección 1 con imagen de fondo -->
            <section>
              <Swiper
                @swiper="onSwiperInit"
                ref="swiperRef"
                :effect="'cube'"
                :grabCursor="true"
                :cubeEffect="{
                  shadow: true,
                  slideShadows: true,
                  shadowOffset: 20,
                  shadowScale: 0.94,
                }"
                :autoplay='{
                            "delay": 300000,
                            "disableOnInteraction": false
                          }'
                :pagination="{
                  clickable: true,
                }"
                :modules="modules"
                :navigation="true"
                @autoplayTimeLeft="onAutoplayTimeLeft"
                class="mySwiper" 
                :speed="1000"
                
              >
                <SwiperSlide v-for="(photo, index) in photos" :key="index"
                  class="sm:w-full content-center" style="cursor: default">
                  <img :src="`banner-index/${photo.name}`" :alt="'Imagen ' + (index +1)" style="height: 70vh; 
                  width: auto; margin: 0 auto;" />
                  <div class="relative inline-flex w-fit 
                      hover:[&>svg]:scale-125 transition-transform duration-300" style="position: absolute; 
                      top: 1em; right: 2rem;">
                    <div
                      class="absolute bottom-auto left-auto right-1 top-1 z-10 inline-block -translate-y-1/2 translate-x-2/4 
                      rotate-0 skew-x-0 skew-y-0 scale-x-100 scale-y-100 whitespace-nowrap rounded-full bg-red-500 px-1 py-1 
                      text-center align-baseline text-xs font-bold leading-none text-white">
                      18
                    </div>
                    <!-- Whatsapp -->
                    <span class="[&>svg]:h-10 [&>svg]:w-10 [&>svg]:fill-[#128c7e] transform-gpu hover:[&>svg]:scale-125 transition-transform"
                        style="cursor: pointer" @mouseenter="stopAutoplay"
                        @mouseleave="startAutoplay">
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        fill="currentColor"
                        viewBox="0 0 448 512">
                        <path
                          d="M380.9 97.1C339 55.1 283.2 32 223.9 32c-122.4 0-222 99.6-222 222 0 39.1 10.2 77.3 29.6 111L0 480l117.7-30.9c32.4 17.7 68.9 27 106.1 27h.1c122.3 0 224.1-99.6 224.1-222 0-59.3-25.2-115-67.1-157zm-157 341.6c-33.2 0-65.7-8.9-94-25.7l-6.7-4-69.8 18.3L72 359.2l-4.4-7c-18.5-29.4-28.2-63.3-28.2-98.2 0-101.7 82.8-184.5 184.6-184.5 49.3 0 95.6 19.2 130.4 54.1 34.8 34.9 56.2 81.2 56.1 130.5 0 101.8-84.9 184.6-186.6 184.6zm101.2-138.2c-5.5-2.8-32.8-16.2-37.9-18-5.1-1.9-8.8-2.8-12.5 2.8-3.7 5.6-14.3 18-17.6 21.8-3.2 3.7-6.5 4.2-12 1.4-32.6-16.3-54-29.1-75.5-66-5.7-9.8 5.7-9.1 16.3-30.3 1.8-3.7 .9-6.9-.5-9.7-1.4-2.8-12.5-30.1-17.1-41.2-4.5-10.8-9.1-9.3-12.5-9.5-3.2-.2-6.9-.2-10.6-.2-3.7 0-9.7 1.4-14.8 6.9-5.1 5.6-19.4 19-19.4 46.3 0 27.3 19.9 53.7 22.6 57.4 2.8 3.7 39.1 59.7 94.8 83.8 35.2 15.2 49 16.5 66.6 13.9 10.7-1.6 32.8-13.4 37.4-26.4 4.6-13 4.6-24.1 3.2-26.4-1.3-2.5-5-3.9-10.5-6.6z" />
                      </svg>
                    </span>
                  </div>
                  <!--<div class="w-20 h-12 bg-blue-500 sm:bg-red-500 md:bg-yellow-500 lg:bg-green-500 xl:bg-current 
                    2xl:bg-purple-700">ffhgkdkkdgh</div> -->
                    <div class="animated-rectangle mx-auto top-80 h-80 sm:w-full sm:top-96 md:max-w-11/12 sm:px-4 sm:top-80
                      2xl:w-7/12 2xl:ml-80 xl:w-7/12 xl:ml-72 lg:w-9/12 lg:ml-36 lg:top-96 lg:h-64 
                      md:w-11/12 md:ml-10 md:top-96 sm:h-64 ">
                      <div class="content-asesoria content-center sm:w-full md:max-w-11/12 sm:px-4" 
                          @mouseenter="stopAutoplay"
                          @mouseleave="startAutoplay">
                          <p style="font-size: 2.2rem;font-family: sans-serif;" class="zoom-text">
                            {{photo.texto}}</p>
                            <button type="button" class="text-white bg-[#FF9119] hover:bg-[#FF9119]/80 focus:ring-4 focus:outline-none 
                              focus:ring-[#FF9119]/50 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center 
                              dark:hover:bg-[#FF9119]/80 dark:focus:ring-[#FF9119]/40 me-2 mb-2  border-2 border-primary-100
                              sm:-mt-8">
                              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" 
                              class="w-3.5 h-3.5 mr-1">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 0 1-2.25 2.25h-15a2.25 2.25 0 0 1-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0 0 19.5 4.5h-15a2.25 2.25 0 0 0-2.25 2.25m19.5 0v.243a2.25 2.25 0 0 1-1.07 1.916l-7.5 4.615a2.25 2.25 0 0 1-2.36 0L3.32 8.91a2.25 2.25 0 0 1-1.07-1.916V6.75" />
                              </svg>
                              Contáctanos
                            </button>
                            <button type="button" class="text-white bg-blue-800 hover:bg-blue-800 focus:ring-4 focus:outline-none 
                              focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center 
                              dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800 border-2 border-primary-100">
                              Conoce más
                              <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
                              </svg>
                            </button>
                        </div>
                    </div>
                  
                </SwiperSlide>
              </Swiper>
            </section>           
            
            <!-- Sección 2 -->
            <section class="section flex content-center mt-12">
              
              <div class="w-1/2 md:w-2/5 xl:w-1/3 2xl:w-1/4 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 
                  dark:border-gray-700 ml-auto mx-1">
                  <a href="#">
                      <img class="rounded-t-lg" src="/img/tecnologias-avanzadas.jpg" alt="" />
                  </a>
                  <div class="p-5">
                      <a href="#">
                          <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">Consultoria en Tecnologias Emergentes</h5>
                      </a>
                      <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">Te ayudamos a estar a la vanguardia de la innovación tecnológica. Nuestro equipo de expertos te asesora en inteligencia artificial, blockchain, IoT y más, transformando desafíos en oportunidades. Adopta las últimas tecnologías y mantén a tu empresa un paso adelante en la era digital con nuestro asesoramiento personalizado. ¡Revoluciona tu camino hacia el éxito con nosotros!</p>
                      <a href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                          Saber mas
                          <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                              <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
                          </svg>
                      </a>
                  </div>
              </div>
              <div class="w-1/2 md:w-2/5 xl:w-1/3 2xl:w-1/4 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 
                  dark:border-gray-700 mr-auto mx-1">
                  <a href="#">
                      <img class="rounded-t-lg" src="/img/automatizacion-procesos.jpg" alt="" />
                  </a>
                  <div class="p-5">
                      <a href="#">
                          <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
                            Automatización de procesos</h5>
                      </a>
                      <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">Optimizamos tus procesos y operaciones, reduciendo costos y errores, mientras aumentamos la productividad y la calidad. Nuestro equipo de expertos está aquí para simplificar y acelerar cada paso de tu proceso. Desata el verdadero potencial de tu empresa con la automatización inteligente y mantén a tu organización siempre un paso adelante en un mercado competitivo. ¡Descubre cómo la automatización puede revolucionar tu negocio hoy mismo!</p>
                      <a href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                          Saber mas
                          <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                              <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
                          </svg>
                      </a>
                  </div>
              </div>
            </section>
            
            <!-- Sección 3 -->
            <section class="section grid grid-cols-1 content-center ">
              <a href="#" class="flex flex-col items-center bg-white border border-gray-200 rounded-lg shadow md:flex-row md:w-4/6 hover:bg-gray-100 dark:border-gray-700 dark:bg-gray-800 dark:hover:bg-gray-700 place-self-center px-4">
                <img class="object-cover w-full rounded-t-lg h-96 md:h-auto md:w-2/5 md:rounded-none md:rounded-s-lg" src="/img/inteligencia-artificial.jpg" alt="">
                <div class="flex flex-col justify-between p-4 leading-normal">
                    <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">Soluciones IA</h5>
                    <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">En un mundo donde la inteligencia artificial está redefiniendo la manera en que hacemos negocios, nuestras soluciones están diseñadas para ayudarte a liderar la revolución tecnológica. Ya sea optimizando procesos, personalizando experiencias de cliente o impulsando la toma de decisiones con datos precisos, nuestras soluciones de IA transformarán tu empresa. Nuestro equipo de expertos en inteligencia artificial trabajará contigo para desarrollar y desplegar tecnologías innovadoras que maximicen la eficiencia y el crecimiento de tu negocio. ¡Descubre cómo la IA puede llevar tu empresa al siguiente nivel con nuestras soluciones personalizadas y vanguardistas!</p>
                </div>
              </a>
            </section>
            <!-- Más secciones según sea necesario -->
            <section class="section flex content-center">
              <div class="md:w-4/6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 
                  dark:border-gray-700 m-auto">
                  <a href="#">
                      <img class="rounded-t-lg" src="/img/software-testing.jpg" alt="" />
                  </a>
                  <div class="w-full bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
                    <div class="sm:hidden">
                      <label for="tabs" class="sr-only">Select tab</label>
                      <select id="tabs" class="bg-gray-50 border-0 border-b border-gray-200 text-gray-900 text-sm rounded-t-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                          <option>Calidad de Software</option>
                          <option>Funcionalidad</option>
                          <option>Seguridad</option>
                      </select>
                    </div>
                    <ul class="hidden text-sm font-medium text-center text-gray-500 divide-x divide-gray-200 rounded-lg sm:flex dark:divide-gray-600 dark:text-gray-400 rtl:divide-x-reverse" id="fullWidthTab" data-tabs-toggle="#fullWidthTabContent" role="tablist">
                        <li class="w-full">
                            <button id="stats-tab" data-tabs-target="#stats" type="button" role="tab" aria-controls="stats" aria-selected="true" @click="activeTab = 'tab-calidad'"
                            class="inline-block w-full p-4 rounded-ss-lg bg-gray-50 hover:bg-gray-100 focus:outline-none dark:bg-gray-700 dark:hover:bg-gray-600">Calidad de Software</button>
                        </li>
                        <li class="w-full">
                            <button id="about-tab" data-tabs-target="#about" type="button" role="tab" aria-controls="about" aria-selected="false" @click="activeTab = 'tab-funcionalidad'"
                            class="inline-block w-full p-4 bg-gray-50 hover:bg-gray-100 focus:outline-none dark:bg-gray-700 dark:hover:bg-gray-600">Funcionalidad</button>
                        </li>
                        <li class="w-full">
                            <button id="faq-tab" data-tabs-target="#faq" type="button" role="tab" aria-controls="faq" aria-selected="false" @click="activeTab = 'tab-seguridad'"
                            class="inline-block w-full p-4 rounded-se-lg bg-gray-50 hover:bg-gray-100 focus:outline-none dark:bg-gray-700 dark:hover:bg-gray-600">Seguridad</button>
                        </li>
                    </ul>
                    <div id="fullWidthTabContent" class="border-t border-gray-200 dark:border-gray-600">
                      <div>
                        <div v-if="activeTab === 'tab-calidad'" class="p-8">
                          <h2 class="mb-3 text-3xl font-extrabold tracking-tight text-gray-900 dark:text-white">Verificacmos la calidad de tu software</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">Nos dedicamos a garantizar que cada línea de código funcione a la perfección, brindando soluciones confiables y robustas. Nuestro equipo de expertos realiza pruebas exhaustivas, asegurando que tu software cumpla con los estándares más altos. Con nosotros, tu software estará siempre un paso adelante, listo para enfrentar cualquier desafío. ¡Confía en nosotros para llevar la calidad de tu software al siguiente nivel! </p>
                          <a href="#" class="inline-flex items-center font-medium text-blue-600 hover:text-blue-800 dark:text-blue-500 dark:hover:text-blue-700">
                              Saber más
                              <svg class=" w-2.5 h-2.5 ms-2 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                                  <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 9 4-4-4-4"/>
                              </svg>
                          </a>
                        </div>
                        <div v-if="activeTab === 'tab-funcionalidad'" class="p-8">
                          <h2 class="mb-3 text-3xl font-extrabold tracking-tight text-gray-900 dark:text-white">Validación integral de los procesos</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">Aseguramos que cada característica de tu aplicación opere de forma correcta. Nuestro equipo de especialistas se dedica a validar que cada componente de tu software funcione según lo previsto, garantizando una experiencia de usuario fluida y sin errores. A través de pruebas exhaustivas y detalladas, identificamos y corregimos cualquier fallo, asegurando que tu producto cumpla con los más altos estándares de calidad. Confía en nosotros para ofrecerte un software funcional y robusto, preparado para satisfacer y superar las expectativas de tus usuarios. ¡Eleva la fiabilidad de tu software con nuestra experiencia en pruebas de funcionalidad!</p>
                          <a href="#" class="inline-flex items-center font-medium text-blue-600 hover:text-blue-800 dark:text-blue-500 dark:hover:text-blue-700">
                              Saber más
                              <svg class=" w-2.5 h-2.5 ms-2 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                                  <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 9 4-4-4-4"/>
                              </svg>
                          </a>
                        </div>
                        <div v-if="activeTab === 'tab-seguridad'"  class="p-8">
                          <h2 class="mb-3 text-3xl font-extrabold tracking-tight text-gray-900 dark:text-white">Evaluaciones de seguridad</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">Protegemos el activo más valioso para tu negocio. En un mundo digital lleno de amenazas, nuestro equipo de expertos se dedica a identificar y neutralizar vulnerabilidades en tu sistema, asegurando que tus datos y operaciones estén siempre a salvo. Realizamos análisis exhaustivos y simulaciones de ataques para garantizar que tu infraestructura sea resistente y confiable. Con nuestras evaluaciones de seguridad, puedes operar con la tranquilidad de saber que tu negocio está protegido contra cualquier amenaza. ¡Confía en nosotros para blindar tu empresa y mantenerla segura en la era digital!</p>
                          <a href="#" class="inline-flex items-center font-medium text-blue-600 hover:text-blue-800 dark:text-blue-500 dark:hover:text-blue-700">
                              Saber más
                              <svg class=" w-2.5 h-2.5 ms-2 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                                  <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 9 4-4-4-4"/>
                              </svg>
                          </a>
                        </div>
                      </div>
                    </div>
                  </div>
              </div>              
            </section>
        </div>
    </div>    
  </template>
  <script setup>
  import { Swiper, SwiperSlide } from 'swiper/vue'
  import 'swiper/css/effect-cube'
  import 'swiper/css/pagination'
  import 'swiper/css/navigation'
  import 'swiper/css'
  import 'swiper/swiper-bundle.css'
  import { ref, onMounted } from 'vue'
  import { Autoplay, Pagination, Navigation, EffectCube } from 'swiper/modules'
  const showImage = ref(false);
  const activeTab = ref('tab-calidad')
  const photos = ref([
    { name: 'asesoria.jpg', texto: 'Impulsamos la innovación con tecnologías emergentes y soluciones empresariales.' },
    { name: 'tecnologia.jpg', texto: 'Transformamos tu empresa con asesoría en calidad y automatización de procesos.' },
    { name: 'codigo.jpg', texto: 'Soluciones empresariales innovadoras para tu empresa frente a un mundo digital.' },
    { name: 'capacitaciones.jpg', texto: 'Maximizamos la eficiencia dentro de la empresa con tecnologías y asesorías personalizadas.' }
  ])
  const swiperRef = ref(null);
  const stopAutoplay = () => {
    console.log('Autoplay stopped 2');
    console.log(swiperRef)
    console.log(swiperRef.value)
    console.log(swiperRef.value.autoplay)
    if (swiperRef.value && swiperRef.value.swiper) {
      swiperRef.value.swiper.autoplay.stop();
    }
  };

  const startAutoplay = () => {
    console.log('Autoplay stopped 4');
    console.log(swiperRef)
    console.log(swiperRef.value)
    console.log(swiperRef.value.autoplay)
    if (swiperRef.value && swiperRef.value.swiper) {
      console.log('Autoplay stopped 5');
      swiperRef.value.swiper.autoplay.start();
    }
  };
  const onSwiperInit = (swiper) => {
    console.log('Swiper instance:', swiper);
    swiperRef.value.swiper = swiper; // Guarda la instancia para uso futuro
  };
  const autoplayConfig = {
                  delay: 1000,
                  disableOnInteraction: false,
                } 
  const modules = ref([Autoplay, Pagination, Navigation, EffectCube])
  onMounted(() => {
    console.log('Swiper instance:', swiperRef.value?.swiper);
    // Mostrar gradualmente la imagen después de que el componente se monta
    setTimeout(() => {
      showImage.value = true;
    }, 400); // Retraso pequeño para que se vea la transición
  });
  </script>
  
  <style>
  .background-image {
    position: relative;
    width: 100%;
    height: 100vh;
    background-image: url('/img/grupo.jpg'); /* Ruta a tu imagen de fondo */
    background-size: cover;
    background-position: center;
    filter: brightness(25%) grayscale(15%); 
    overflow-y: none;
    opacity: 0; /* Inicialmente transparente */
    transition: opacity 5s ease; /* Transición suave para la opacidad */
  }
  
  .background-image.show-image {
    opacity: 1; /* Opacidad normal */
  }
  
  .content {
    position: relative;
    z-index: 1;
    padding: 0;
  }
  
  .section {
    padding: 0 0 40px 0;
    background-color: #ffffff;
    
  }
  
  .section h2 {
    font-size: 24px;
    margin-bottom: 10px;
  }
  
  .section p {
    font-size: 16px;
    line-height: 1.6;
  }
  .zoom-text {
    animation: zoomIn 3s ease-out forwards;
    }
  .animated-rectangle {
    position: absolute;
    /*width: 700px;
    height: 300px;*/
    background-color: rgba(0, 0, 0, 0.8); /* Fondo inicial difuminado */
    backdrop-filter: blur(10px); /* Efecto de difuminado */
    opacity: 0; /* Inicialmente invisible */
    /* Animación */
    animation: fadeIn 4s ease-out forwards;
    border: 5px solid white;
    border-top-left-radius: 30px;
    border-bottom-right-radius: 30px;
}

.content-asesoria {
  position: relative;
  z-index: 1;
  text-align: center;
  color: white;
  font-size: 3.5rem;
  opacity: 1;
}

@keyframes fadeIn {
  0% {
    background-color: rgba(0, 0, 0, 0.8); /* Inicio con fondo difuminado */
    backdrop-filter: blur(10px); /* Inicio con efecto de difuminado */
    opacity: 0; /* Inicio invisible */
  }
  100% {
    background-color: rgba(0, 0, 0, 0.4); /* Final con fondo menos difuminado */
    backdrop-filter: blur(0px); /* Final sin efecto de difuminado */
    opacity: 1; /* Final visible */
  }
}
@keyframes zoomIn {
  0% {
    transform: scale(1.5); /* Escala inicial del texto (más grande) */
    opacity: 0;
  }
  100% {
    transform: scale(1); /* Escala final del texto (tamaño normal) */
    opacity: 1;
  }
}
  </style>