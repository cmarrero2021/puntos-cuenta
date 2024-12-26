<template>
  <div>
    <!-- Elementos sin hijos -->
    <q-item
      clickable
      @click="navigate"
      v-if="!children || children.length === 0"
      :class="{'q-ml-xl': isChild}"
    >
      <q-item-section v-if="icon" avatar>
        <q-icon :name="icon" />
      </q-item-section>

      <q-item-section>
        <q-item-label>{{ title }}</q-item-label>
        <q-item-label caption v-if="caption">{{ caption }}</q-item-label>
      </q-item-section>
    </q-item>

    <!-- Elementos con hijos -->
    <q-expansion-item v-else :label="title" :icon="icon" expand-separator>
      <DrawerLink
        v-for="child in children"
        :key="child.title"
        :title="child.title"
        :route="child.route"
        :icon="child.icon"
        :caption="child.caption"
        :is-child="true"
        @navigate="navigate"
      />
    </q-expansion-item>
  </div>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  caption: {
    type: String,
    default: '',
  },
  route: {
    type: String,
    default: null,
  },
  icon: {
    type: String,
    default: '',
  },
  children: {
    type: Array,
    default: () => [],
  },
  isChild: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(['navigate']);

const navigate = () => {
  if (props.route) {
    emit('navigate', props.route);
  }
};
</script>
