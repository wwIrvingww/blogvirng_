<template>
  <div>
    <div class="sitio-web">
      <div class="paginas">
        <TopBar :onRouteChange="handleRouteChange" />
        <Router :ruta="rutaActual" :navigate="handleRouteChange" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { LoginProvider } from './Hooks/useLogin'
import Router from './components/Router/Router.vue'
import TopBar from './components/TopBar/TopBar.vue'

const rutaActual = ref(window.location.pathname)

const handleRouteChange = (route) => {
  rutaActual.value = route
  window.history.pushState({}, '', route)
}

onMounted(() => {
  console.log('Se ha montado el componente')
  console.log('RUTA ACTUAL: ', window.location.pathname)
  rutaActual.value = window.location.pathname
  console.log(window.location)
})
</script>

<style scoped>
/* Estilos específicos de este componente */
</style>
