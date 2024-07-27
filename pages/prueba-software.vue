<template>
    <div>
      <section class="section" ref="section1">
          <div class="background-image"  :class="{ 'show-image': showImage }">
  
          </div>
          <div class="animated-rectangle">
              <div class="content-asesoria">
                  <p style="font-size: 3.2rem;font-family: sans-serif;" class="zoom-text">
                      Pruebas de Calidad de Software</p>
              </div>
          </div>
      </section>
    </div>
  </template>
  
  <script setup>
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