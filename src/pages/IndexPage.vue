<template>
  <q-page class="row justify-center relative-position q-pt-md">
    <input
      v-model="filter"
      :style="{ width: '200px', zIndex: 10000, top: '0.5rem', right: '0.5rem' }"
      class="fixed-top-right q-pa-sm shadow-1 rounded-borders no-border"
      placeholder="Buscar canción ..."
    />
    <q-table
      class="q-my-xl"
      style="width: 95vw"
      flat
      bordered
      title="Canciones"
      :rows="rows"
      :columns="columns"
      row-key="name"
      :filter="filter"
      :rows-per-page-options="[10, 20, 30, 50, 0]"
    >
    </q-table>
    <div class="text-grey-5">powered by @jeff.ssl</div>
  </q-page>
</template>

<script setup lang="ts">
//eslint-disable @typescript-eslint/no-explicit-any
import { onBeforeMount, ref } from 'vue';
import listaCanciones from '../../lista_canciones/listaCanciones.json';

interface ISong {
  NUM: number;
  TITULO: string;
  ARTISTA: string;
  GENERO: string;
}
interface Icolumn {
  name: string;
  label: string;
  field: string | ((row: any) => any);
  required?: boolean;
  align?: 'left' | 'right' | 'center';
  sortable?: boolean;
  sort?: (a: any, b: any, rowA: any, rowB: any) => number;
  rawSort?: (a: any, b: any, rowA: any, rowB: any) => number;
  sortOrder?: 'ad' | 'da';
  format?: (val: any, row: any) => any;
  style?: string | ((row: any) => string);
  classes?: string | ((row: any) => string);
  headerStyle?: string;
  headerClasses?: string;
}
const filter = ref('');
const rows = ref<ISong[]>();
const columns: Icolumn[] = [
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
</script>
<style lang="scss" scoped>
input:focus {
  outline: none;
}
</style>
