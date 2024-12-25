<template>
  <q-layout view="hHh lpR fFf">
    <q-header reveal elevated class="bg-teal-3 text-blue-grey-9">
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

    <!-- <q-footer reveal elevated class="bg-green-3 text-dark">
      <q-toolbar style="flex: 1; text-align: center;">
        <q-toolbar-title  style="font-size: 12px;">
          <div>República Bolivariana de Venezuela. Ministerio del Poder Popular para Adultos y Adultas Mayores Abuelos y Abuelas de la Patria. Oficina de Tecnologías de la Comunicación y la Información, 2025</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer> -->
    <q-footer reveal elevated class="bg-green-3 text-dark footer">
      <q-toolbar style="flex: 1; text-align: center">
        <q-toolbar-title style="font-size: 12px">
          <!-- Texto para pantallas estrechas -->

          <div class="responsive-text">
            República Bolivariana de Venezuela.<br />
            Ministerio del Poder Popular para Adultos y Adultas Mayores<br />
            Abuelos y Abuelas de la Patria.<br />
            Oficina de Tecnologías de la Comunicación y la Información<br />
            2025
          </div>

          <!-- Texto para pantallas medias y superiores -->

          <div class="wide-text">
            República Bolivariana de Venezuela. Ministerio del Poder Popular
            para Adultos y Adultas Mayores Abuelos y Abuelas de la Patria.
            Oficina de Tecnologías de la Comunicación y la Información, 2025
          </div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
};
</script>
<style scoped>
.responsive-text {
  display: block;
}

@media (min-width: 960px) {
  .responsive-text {
    display: none; /* Oculta el texto en pantallas medianas y grandes */
  }
  .wide-text {
    display: block;
  }
}

@media (max-width: 959px) {
  .responsive-text {
    display: block; /* Muestra el texto en pantallas pequeñas */
  }
  .wide-text {
    display: none; /* Muestra el texto en pantallas pequeñas */
  }
}
.footer {
  display: block; /* Muestra el footer por defecto */
}

/* Oculta el footer en pantallas estrechas y en orientación horizontal */

@media (max-width: 959px) and (orientation: landscape) {
  .footer {
    display: none; /* Oculta el footer */
  }
}
</style>
