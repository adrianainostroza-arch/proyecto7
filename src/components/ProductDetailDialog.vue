<script setup>
import { computed } from 'vue'
import { formatearPrecio, iconoCategoria } from '@/utils'

const props = defineProps({
  modelValue: { type: Boolean, default: false },
  producto: { type: Object, default: null }
})

const emit = defineEmits(['update:modelValue'])

const abierto = computed({
  get: () => props.modelValue,
  set: (valor) => emit('update:modelValue', valor)
})
</script>

<template>
  <v-dialog v-model="abierto" max-width="520">
    <v-card v-if="producto" data-testid="detalle-producto">
      <v-card-title class="d-flex align-center">
        <v-icon :icon="iconoCategoria(producto.categoria)" class="mr-2" aria-hidden="true" />
        {{ producto.nombre }}
      </v-card-title>
      <v-card-subtitle>{{ producto.marca }} · {{ producto.categoria }}</v-card-subtitle>

      <v-card-text>
        <p class="mb-4">{{ producto.descripcion }}</p>
        <v-list density="compact">
          <v-list-item title="Precio" :subtitle="formatearPrecio(producto.precio)" />
          <v-list-item title="Unidades disponibles" :subtitle="String(producto.stock)" />
          <v-list-item title="Código" :subtitle="`#${producto.id}`" />
        </v-list>
      </v-card-text>

      <v-card-actions>
        <v-spacer />
        <v-btn color="primary" variant="text" @click="abierto = false">Cerrar</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
