<template>
  <q-page class="q-pa-lg bg-grey-1">

    <h4 class="text-h5 text-primary text-center q-mb-md">
      Popis svih knjiga
    </h4>

    <q-table
      title="Knjige u knjižnici"
      :rows="rows"
      :columns="columns"
      row-key="id"
      flat
      bordered
      separator="horizontal"
      :pagination="{ rowsPerPage: 5 }"
      class="bg-white shadow-2 rounded-borders"
    >
    
      <template v-slot:body-cell-slika="props">
        <q-td :props="props">
          <img
            :src="props.row.slika"
            alt="Slika knjige"
            style="width: 60px; height: auto; border-radius: 6px;"
          />
        </q-td>
      </template>

      <template v-slot:body-cell-status="props">
        <q-td :props="props">
          <q-chip
            :color="props.row.status === 'Slobodna' ? 'green' : 'red'"
            text-color="white"
            size="sm"
          >
            {{ props.row.status }}
          </q-chip>
        </q-td>
      </template>
    </q-table>

  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const columns = [
  {
    name: 'id',
    label: 'ID',
    field: 'id',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'naslov',
    label: 'Naslov',
    field: 'naslov',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'autor',
    label: 'Autor',
    field: 'autor',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'opis',
    label: 'Opis',
    field: 'opis',
    align: 'left',
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'slika',
    label: 'Slika',
    field: 'slika',
    align: 'center',
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  },
  {
    name: 'status',
    label: 'Status',
    field: 'status',
    align: 'center',
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px' }
  }
]

const rows = ref([
  {
    id: 1,
    naslov: 'Raskrižje gavranova',
    autor: 'Andrzej Sapkowski',
    opis: 'Fantastični roman iz poznatog Witcher serijala.',
    slika: 'https://m.media-amazon.com/images/I/81rcURiyM2L._AC_UF1000,1000_QL80_.jpg',
    status: 'Slobodna'
  },
  {
    id: 2,
    naslov: 'Gospodar prstenova: Prstenova družina',
    autor: 'J.R.R. Tolkien',
    opis: 'Prvi dio epske trilogije o borbi protiv Saurona.',
    slika: 'https://upload.wikimedia.org/wikipedia/en/8/8e/The_Fellowship_of_the_Ring_cover.gif',
    status: 'Zauzeta'
  },
  {
    id: 3,
    naslov: 'The Name of the Wind',
    autor: 'Patrick Rothfuss',
    opis: 'Priča o Kvotheu, talentiranom mladom čarobnjaku i glazbeniku.',
    slika: 'https://m.media-amazon.com/images/S/compressed.photo.goodreads.com/books/1704917687i/186074.jpg',
    status: 'Slobodna'
  },
  {
    id: 4,
    naslov: 'Mistborn: The Final Empire',
    autor: 'Brandon Sanderson',
    opis: 'Prvi dio Mistborn serijala, epska fantazija o pobuni protiv tiranskog vladara.',
    slika: 'https://m.media-amazon.com/images/I/811qBmIYTFL._AC_UF1000,1000_QL80_.jpg',
    status: 'Zauzeta'
  },
  {
    id: 5,
    naslov: 'The Lies of Locke Lamora',
    autor: 'Scott Lynch',
    opis: 'Priča o genijalnom lopovu i njegovoj bandi u fantastičnom gradu Camorr.',
    slika: 'https://www.menartshop.hr/wp-content/uploads/2025/04/b595b1b1-9cdb-4245-8a4a-fbc0ca9fda6b.png',
    status: 'Slobodna'
  },
{
  id: 6,
  naslov: 'Eragon',
  autor: 'Christopher Paolini',
  opis: 'Prva knjiga iz Inheritance Cycle serijala, avantura mladog jahača zmaja.',
  slika: 'https://upload.wikimedia.org/wikipedia/en/c/ce/Eragon_book_cover.png',
  status: 'Slobodna'
  },
  {
    id: 7,
    naslov: 'The Hobbit',
    autor: 'J.R.R. Tolkien',
    opis: 'Avanture Bilba Bagginsa i putovanje kroz Srednju Zemlju.',
    slika: 'https://m.media-amazon.com/images/I/71jD4jMityL._AC_UF1000,1000_QL80_.jpg',
    status: 'Zauzeta'
  }
])
</script>

<style scoped>
.q-table {
  border-radius: 12px;
}
</style>