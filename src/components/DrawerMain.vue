<template>
  <q-drawer
    :model-value="drawerOpen"
    @update:model-value="updateDrawer"
    behavior="desktop"
    side="left"
    overlay
    bordered
  >
    <q-list>
      <DrawerLink
        v-for="link in links"
        :key="link.title"
        :title="link.title"
        :icon="link.icon"
        :caption="link.caption"
        :route="link.route"
        :children="link.children"
        @navigate="handleNavigation"
      />
    </q-list>
  </q-drawer>
</template>

<script setup>
import { useRouter } from 'vue-router';
import DrawerLink from './DrawerLink.vue';

const props = defineProps({
  drawerOpen: {
    type: Boolean,
    required: true,
  },
});

const emit = defineEmits(['update:drawerOpen']);

const router = useRouter();

const links = [
  { title: 'Inicio', icon: 'home', route: 'inicio' },
  {
    title: 'Puntos de Cuenta',
    icon: 'list',
    children: [
      { title: 'Punto de Cuenta', route: 'puntos' },
      { title: 'Revisar Punto de Cuenta', route: 'revisar-puntos' },
      { title: 'Aprobar Punto de Cuenta', route: 'aprobar-puntos' },
    ],
  },
  {
    title: 'Auxiliares',
    icon: 'layers',
    children: [
      { title: 'Unidades Administrativas', route: 'unidades-administrativas' },
      { title: 'Áreas', route: 'areas' },
      { title: 'Responsables', route: 'responsables' },
      { title: 'Tipos de Puntos de Cuenta', route: 'tipos' },
    ],
  },
  {
    title: 'Administración',
    icon: 'settings',
    children: [
      { title: 'Usuarios', route: 'usuarios' },
      { title: 'Auditoría', route: 'auditoria' },
    ],
  },
];

const updateDrawer = (value) => {
  emit('update:drawerOpen', value);
};

const handleNavigation = (route) => {
  // router.push(`/${route}`);
  emit('update:drawerOpen', false); // Cierra el drawer después de navegar

  console.log("pepe");
  Notify.create({
    message: 'Navegando a ' + route,
    color: 'primary',
    position: 'top',
  });
};
</script>
