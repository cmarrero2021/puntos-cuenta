<template>
  <q-layout view="hHh lpR fFf">

    <q-header reveal elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="swap_horiz" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <!-- <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar> -->
          Puntos de Cuenta
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" side="left" overlay bordered>
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer reveal elevated class="bg-grey-8 text-white">
      <q-toolbar class="bg-white text-black" style="flex: 1; text-align: center;">
        <q-toolbar-title  style="font-size: 12px;">
          <div>República Bolivariana de Venezuela. Ministerio del Poder Popular para Adultos y Adultas Mayores Abuelos y Abuelas de la Patria. Oficina de Tecnologías de la Comunicación y la Información, 2025</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
}
</script>
