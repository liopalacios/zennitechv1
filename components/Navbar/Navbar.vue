<template>
    <header class="bg-white">
      <nav class="mx-auto flex max-w-7xl items-center justify-between p-6 lg:px-8" aria-label="Global">
        <div class="flex lg:flex-1">
          <a href="#" class="-m-1.5 p-1.5">
            <span class="sr-only">Company</span>
            <NuxtLink to="/">
                <img class="h-8 w-auto" src="/img/mailgun-icon.svg" alt="" />
            </NuxtLink>
            
          </a>
        </div>
        <div class="flex lg:hidden">
          <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700" 
            @click="mobileMenuOpen = true">
            <span class="sr-only">Open main menu</span>
            <Bars3Icon class="h-6 w-6" aria-hidden="true" />
          </button>
        </div>
        <PopoverGroup class="hidden lg:flex lg:gap-x-12">                 
          <NuxtLink to="/nosotros" class="text-sm font-semibold leading-6 text-gray-900">Nosotros</NuxtLink>
          <Popover class="relative" ref="popoverRef"  @mouseenter="openPopover">
            <PopoverButton class="flex items-center gap-x-1 text-sm font-semibold leading-6 text-gray-900">
              Servicios
              <ChevronDownIcon class="h-5 w-5 flex-none text-gray-400" aria-hidden="true" />
            </PopoverButton>  
            <transition enter-active-class="transition ease-out duration-200" enter-from-class="opacity-0 translate-y-1" 
                enter-to-class="opacity-100 translate-y-0" leave-active-class="transition ease-in duration-150" 
                leave-from-class="opacity-100 translate-y-0" leave-to-class="opacity-0 translate-y-1">
              <PopoverPanel v-if="popoverOpen" class="absolute -left-8 top-full z-10 mt-3 w-screen max-w-md overflow-hidden 
                    rounded-3xl bg-white shadow-lg ring-1 ring-gray-900/5">
                <div class="p-4">
                  <div v-for="item in products" :key="item.name" @click="closePopover" class="group relative flex items-center gap-x-6 rounded-lg p-4 text-sm leading-6 hover:bg-gray-50">
                    <div class="flex h-11 w-11 flex-none items-center justify-center rounded-lg bg-gray-50 group-hover:bg-white">
                      <component :is="item.icon" class="h-6 w-6 text-gray-600 group-hover:text-indigo-600" aria-hidden="true" />
                    </div>                    
                    <div class="flex-auto">                        
                      <NuxtLink :href="item.href" class="block font-semibold text-gray-900">
                        {{ item.name }}
                        <span class="absolute inset-0" />
                      </NuxtLink>
                      <p class="mt-1 text-gray-600">{{ item.description }}</p>
                    </div>
                  </div>
                </div>
                <div class="grid grid-cols-2 divide-x divide-gray-900/5 bg-gray-50">
                  <a v-for="item in callsToAction" :key="item.name" :href="item.href" class="flex items-center justify-center gap-x-2.5 p-3 text-sm font-semibold leading-6 text-gray-900 hover:bg-gray-100">
                    <component :is="item.icon" class="h-5 w-5 flex-none text-gray-400" aria-hidden="true" />
                    {{ item.name }}
                  </a>
                </div>
              </PopoverPanel>
            </transition>
          </Popover>
          <NuxtLink to="/clientes" class="text-sm font-semibold leading-6 text-gray-900">Clientes</NuxtLink>
          <NuxtLink to="/capacitaciones" class="text-sm font-semibold leading-6 text-gray-900">Academia</NuxtLink>
          <NuxtLink to="/nuestras-politicas" class="text-sm font-semibold leading-6 text-gray-900">Blog</NuxtLink>
          <NuxtLink to="/servicios" class="text-sm font-semibold leading-6 text-gray-900">Contacto</NuxtLink>
          <a href="#" class="text-sm font-semibold leading-6 text-gray-900"></a>
          <a href="#" class="text-sm font-semibold leading-6 text-gray-900"></a>
          <a href="#" class="text-sm font-semibold leading-6 text-gray-900"></a>
          <a href="#" class="text-sm font-semibold leading-6 text-gray-900"></a>
        </PopoverGroup>
        <div class="hidden lg:flex lg:flex-1 lg:justify-end">
          <a href="#" class="text-sm font-semibold leading-6 text-gray-900">Usuario <span aria-hidden="true">&rarr;</span></a>
        </div>
      </nav>
      <Dialog class="lg:hidden" @close="mobileMenuOpen = false" :open="mobileMenuOpen">
        <div class="fixed inset-0 z-10" />
        <DialogPanel class="fixed inset-y-0 right-0 z-10 w-full overflow-y-auto bg-white px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10">
          <div class="flex items-center justify-between">
            <a href="#" class="-m-1.5 p-1.5">
              <span class="sr-only">Your Company</span>
              <img class="h-8 w-auto" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600" alt="" />
            </a>
            <button type="button" class="-m-2.5 rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = false">
              <span class="sr-only">Close menu</span>
              <XMarkIcon class="h-6 w-6" aria-hidden="true" />
            </button>
          </div>
          <div class="mt-6 flow-root">
            <div class="-my-6 divide-y divide-gray-500/10">
              <div class="space-y-2 py-6">
                <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Nosotros</a>
                <Disclosure as="div" class="-mx-3" v-slot="{ open }">
                  <DisclosureButton class="flex w-full items-center justify-between rounded-lg py-2 pl-3 pr-3.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">
                    Servicios
                    <ChevronDownIcon :class="[open ? 'rotate-180' : '', 'h-5 w-5 flex-none']" aria-hidden="true" />
                  </DisclosureButton>
                  <DisclosurePanel class="mt-2 space-y-2">
                    <DisclosureButton v-for="item in [...products, ...callsToAction]" :key="item.name" as="a" :href="item.href" class="block rounded-lg py-2 pl-6 pr-3 text-sm font-semibold leading-7 text-gray-900 hover:bg-gray-50">{{ item.name }}</DisclosureButton>
                  </DisclosurePanel>
                </Disclosure>
                <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Clientes</a>
                <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Academia</a>
                <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Blog</a>
                <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Contacto</a>
              </div>
              <div class="py-6">
                <a href="#" class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Usuario</a>
              </div>
            </div>
          </div>
        </DialogPanel>
      </Dialog>
    </header>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import {
    Dialog,
    DialogPanel,
    Disclosure,
    DisclosureButton,
    DisclosurePanel,
    Popover,
    PopoverButton,
    PopoverGroup,
    PopoverPanel,
  } from '@headlessui/vue'
  import {
    ArrowPathIcon,
    Bars3Icon,
    ChartPieIcon,
    CursorArrowRaysIcon,
    FingerPrintIcon,
    SquaresPlusIcon,
    XMarkIcon,
  } from '@heroicons/vue/24/outline'
  import { ChevronDownIcon, PhoneIcon, PlayCircleIcon } from '@heroicons/vue/20/solid'
  
  const products = [
    
    { name: 'Consultoria en Tecnologias Emergentes', description: 'Asesoría en nuevas tecnología', href: '/asesoria-software', icon: SquaresPlusIcon },
    { name: 'Automatizacion de Procesos', description: 'Optimización automática de procesos', href: '/producto-software', icon: ArrowPathIcon },
    { name: 'Soluciones de IA', description: 'Soluciones basadas en Inteligencia Artificial', href: '/soluciones-ia', icon: ArrowPathIcon },
    { name: 'Pruebas de Calidad', description: 'Verificación de la calidad de software', href: '/prueba-software', icon: ChartPieIcon },
    { name: 'Pruebas de Funcionalidad', description: 'Validación integral de los procesos', href: '/pruebas-funcionales', icon: CursorArrowRaysIcon },
    { name: 'Pruebas de seguridad', description: 'Evaluación de la Seguridad de tu software', href: '/pruebas-seguridad', icon: FingerPrintIcon }
  ]
  const callsToAction = [
    { name: 'Ver demostración', href: '#', icon: PlayCircleIcon },
    { name: 'Contacto', href: '#', icon: PhoneIcon },
  ]
  
  const mobileMenuOpen = ref(false)
  const popoverOpen = ref(null)
  const closePopover = () => {
    popoverOpen.value = false
  }
  const openPopover = () => {
    popoverOpen.value = true
  }
  </script>