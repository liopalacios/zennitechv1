<template>
    <div>
        <section class="section flex content-center">
              <div class="md:w-4/6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 
                  dark:border-gray-700 m-auto">
                  <a href="#">
                      <img class="rounded-t-lg" src="/img/nosotros.jpg" alt="" width="100%" />
                  </a>
                  <div class="w-full bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
                    <div class="sm:hidden">
                      <label for="tabs" class="sr-only">Select tab</label>
                      <select id="tabs" class="bg-gray-50 border-0 border-b border-gray-200 text-gray-900 text-sm rounded-t-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                        <option>Objetivos</option>  
                        <option>Capacidades</option>
                        <option>Experiencia</option>                          
                      </select>
                    </div>
                    <ul class="hidden text-sm font-medium text-center text-gray-500 divide-x divide-gray-200 rounded-lg sm:flex dark:divide-gray-600 dark:text-gray-400 rtl:divide-x-reverse" id="fullWidthTab" data-tabs-toggle="#fullWidthTabContent" role="tablist">
                        <li class="w-full">
                            <button id="stats-tab" data-tabs-target="#stats" type="button" role="tab" aria-controls="stats" aria-selected="true" @click="activeTab = 'tab-calidad'"
                            class="inline-block w-full p-4 rounded-ss-lg bg-gray-50 hover:bg-gray-100 focus:outline-none dark:bg-gray-700 dark:hover:bg-gray-600">Objetivos</button>
                        </li>
                        <li class="w-full">
                            <button id="about-tab" data-tabs-target="#about" type="button" role="tab" aria-controls="about" aria-selected="false" @click="activeTab = 'tab-funcionalidad'"
                            class="inline-block w-full p-4 bg-gray-50 hover:bg-gray-100 focus:outline-none dark:bg-gray-700 dark:hover:bg-gray-600">Capacidades</button>
                        </li>
                        <li class="w-full">
                            <button id="faq-tab" data-tabs-target="#faq" type="button" role="tab" aria-controls="faq" aria-selected="false" @click="activeTab = 'tab-seguridad'"
                            class="inline-block w-full p-4 rounded-se-lg bg-gray-50 hover:bg-gray-100 focus:outline-none dark:bg-gray-700 dark:hover:bg-gray-600">Experiencia</button>
                        </li>
                    </ul>
                    <div id="fullWidthTabContent" class="border-t border-gray-200 dark:border-gray-600">
                      <div>
                        <div v-if="activeTab === 'tab-calidad'" class="p-8">
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Fomentar las Buenas Prácticas</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">Promovemos la adopción de buenas prácticas en la gestión de proyectos y en el desarrollo de software. Esto incluye la implementación de metodologías ágiles, estándares de calidad y procesos de mejora continua que aseguren la eficiencia y efectividad en todas las fases de los proyectos tecnológicos. Asi tambien garantizar que el area de sistemas de cada empresa adopte una cultura de calidad de productos. Esto mediante charlas, capacitaciones, publicaciones y material didactico propio de la empresa.</p>
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Desarrollar Talento y alta competitividad:</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">Nos enfocamos en identificar y cultivar el talento dentro de las empresas, proporcionando las herramientas y el conocimiento necesario para que los equipos sean altamente competitivos. A través de programas de capacitación avanzados y la implementación de estrategias tecnológicas efectivas, ayudamos a las empresas a construir una base sólida de talento que puede innovar y adaptarse rápidamente a los cambios del mercado, asegurando así una posición competitiva fuerte y sostenida.</p>
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Productos de Alta Calidad:</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">Nuestro compromiso es entregar productos y soluciones de alta calidad que superen las expectativas de nuestros clientes. Esto se logra mediante un riguroso control de calidad, pruebas exhaustivas y una atención meticulosa a los detalles, garantizando que cada solución sea robusta, segura y perfectamente adaptada a las necesidades específicas de cada cliente. Garantizamos la cobertura del 100% de los requerimientos del usurio dueño del producto.</p>
                          
                        </div>
                        <div v-if="activeTab === 'tab-funcionalidad'" class="p-8">
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Innovación y Adaptabilidad Tecnológica:</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">La capacidad de innovar y adaptarse rápidamente a las nuevas tecnologías es esencial para una empresa que brinda servicios de asesoría tecnológica. Esta cualidad permite a la empresa mantenerse a la vanguardia de las tendencias tecnológicas, ofreciendo soluciones modernas y efectivas a sus clientes. La adaptabilidad implica no solo la implementación de nuevas tecnologías, sino también la habilidad de integrar estas tecnologías en los procesos existentes de manera eficiente y sin interrupciones.</p>
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Expertise y Conocimiento Especializado:</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">El conocimiento profundo y especializado en diversas áreas de la tecnología es crucial para proporcionar asesoría de alta calidad y capacitaciones efectivas. Esto incluye expertos en desarrollo de software, ciberseguridad, gestión de proyectos tecnológicos, inteligencia artificial y más. Tener un equipo de profesionales altamente capacitados y con experiencia en la industria garantiza que la empresa pueda abordar una amplia gama de desafíos tecnológicos y ofrecer soluciones precisas y adecuadas para cada cliente.</p>
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Orientación al Cliente y Personalización del Servicio:</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">La capacidad de entender y adaptarse a las necesidades específicas de cada cliente es una cualidad fundamental. Esto implica una comunicación abierta y efectiva con los clientes, comprensión de sus objetivos y desafíos particulares, y la personalización de las soluciones y capacitaciones ofrecidas. Una fuerte orientación al cliente asegura que cada proyecto y servicio se alinee perfectamente con las expectativas y requisitos del cliente, lo que resulta en una mayor satisfacción y éxito a largo plazo.</p>
                          
                        </div>
                        <div v-if="activeTab === 'tab-seguridad'"  class="p-8">
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Transformación Digital Integral para una Empresa Multinacional:</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">La empresa lideró un proyecto de transformación digital para una multinacional, optimizando sus procesos internos y mejorando su infraestructura tecnológica. Este proyecto incluyó la implementación de sistemas ERP y CRM, la migración a la nube y la automatización de procesos clave. Como resultado, la empresa cliente experimentó una mejora significativa en la eficiencia operativa, una reducción en los costos operativos y una mayor agilidad para responder a las demandas del mercado.</p>
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Programas de Capacitación en Ciberseguridad:</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">La empresa diseña e imparte un extenso programa de capacitación en ciberseguridad, capacitando a más de 200 empleados en prácticas de seguridad digital, gestión de riesgos y respuesta a incidentes. Este programa incluyó módulos teóricos y prácticos, simulaciones de ataques cibernéticos y evaluaciones continuas para asegurar la comprensión y aplicación de los conocimientos adquiridos. Como resultado, la agencia mejoró significativamente su postura de seguridad y su capacidad para prevenir y responder a amenazas cibernéticas.</p>
                          <h2 class="mb-3 text-2xl font-extrabold tracking-tight text-gray-900 dark:text-white">Desarrollo e Implementación de Software Personalizado:</h2>
                          <p class="mb-3 text-gray-500 dark:text-gray-400">Desarrollo e implementación de soluciones de software personalizados, destinada a mejorar la gestión de flotas y la eficiencia de las operaciones. Esta solución incluyó un sistema de seguimiento en tiempo real, optimización de rutas y gestión de inventarios, integrando datos de múltiples fuentes para proporcionar información precisa y en tiempo real. La implementación de esta solución resultó en una mejora notable en la puntualidad de las entregas, una reducción de los costos de combustible y una mayor satisfacción del cliente final.</p>
                          
                        </div>
                      </div>
                    </div>
                  </div>
              </div>              
            </section>
    </div>  
</template>

<script setup>
 const activeTab = ref('tab-calidad')
</script>

<style>

</style>