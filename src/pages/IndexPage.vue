<template>
  <q-page class="row items-center justify-center">
    <q-table
      style="width: 95vw"
      flat
      bordered
      title="Canciones"
      :rows="rows"
      :columns="columns"
      row-key="name"
      :filter="filter"
      :rows-per-page-options="[0]"
    >
      <template v-slot:top-right>
        <q-input
          borderless
          dense
          debounce="300"
          v-model="filter"
          placeholder="Search"
        >
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
      </template>
    </q-table>
  </q-page>
</template>

<script setup lang="ts">
import { computed, onBeforeMount, ref } from 'vue';
import listaCanciones from '../../lista_canciones/listaCanciones.json';

interface ISong {
  NUM: number;
  TITULO: string;
  ARTISTA: string;
  GENERO: string;
}

const filter = ref('');
const rows = ref<ISong[]>();
const columns = [
  {
    name: 'NUM',
    required: true,
    label: 'NUM.',
    align: 'left',
    field: 'NUM',
    sortable: true,
  },
  {
    name: 'TITULO',
    align: 'center',
    label: 'TITULO',
    field: 'TITULO',
    sortable: true,
  },
  {
    name: 'ARTISTA',
    align: 'center',
    label: 'ARTISTA',
    field: 'ARTISTA',
    sortable: true,
  },
  {
    name: 'GENERO',
    align: 'center',
    label: 'GENERO',
    field: 'GENERO',
    sortable: true,
  },
];
onBeforeMount(() => {
  rows.value = listaCanciones;
});

// const rows = [
//   {
//     name: 'Frozen Yogurt',
//     calories: 159,
//     fat: 6.0,
//     carbs: 24,
//   },
//   {
//     name: 'Ice cream sandwich',
//     calories: 237,
//     fat: 9.0,
//     carbs: 37,
//   },
//   {
//     name: 'Eclair',
//     calories: 262,
//     fat: 16.0,
//     carbs: 23,
//   },
//   {
//     name: 'Cupcake',
//     calories: 305,
//     fat: 3.7,
//     carbs: 67,
//   },
//   {
//     name: 'Gingerbread',
//     calories: 356,
//     fat: 16.0,
//     carbs: 49,
//   },
//   {
//     name: 'Jelly bean',
//     calories: 375,
//     fat: 0.0,
//     carbs: 94,
//   },
//   {
//     name: 'Lollipop',
//     calories: 392,
//     fat: 0.2,
//     carbs: 98,
//   },
//   {
//     name: 'Honeycomb',
//     calories: 408,
//     fat: 3.2,
//     carbs: 87,
//   },
//   {
//     name: 'Donut',
//     calories: 452,
//     fat: 25.0,
//     carbs: 51,
//   },
//   {
//     name: 'KitKat',
//     calories: 518,
//     fat: 26.0,
//     carbs: 65,
//   },
// ];

// const filtrarCanciones = computed(() => {
//   if (filtroEstados.value.length === 0) {
//     return rowTramites.value;
//   } else {
//     if (!rowTramites.value) return;
//     return rowTramites.value.filter((item) =>
//       filtroEstados.value.includes(item.desC_ESTA_TRA),
//     );
//   }
// });
</script>
