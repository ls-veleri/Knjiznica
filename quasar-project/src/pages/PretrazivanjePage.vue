<template>
  <q-page class="q-pa-md">

    <div class="q-gutter-md">
      <q-input
        v-model="searchQuery"
        label="Unesi pojam za pretraživanje"
        outlined
        clearable
      />

      <q-option-group
        v-model="searchBy"
        :options="searchOptions"
        type="radio"
        inline
      />

      <q-btn
        label="Traži"
        color="primary"
        @click="searchBooks"
      />
    </div>

    <q-table
      :rows="filteredBooks"
      :columns="columns"
      row-key="id"
      flat
      bordered
      class="q-mt-md"
      :pagination="{ rowsPerPage: 5 }"
    >
      <template v-slot:body-cell-slika="props">
        <q-td :props="props">
          <img :src="props.row.slika" alt="slika knjige" style="height: 100px;">
        </q-td>
      </template>
    </q-table>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const rows = ref([
  {
    id: 1,
    naslov: 'Raskrižje gavranova',
    autor: 'Andrzej Sapkowski',
    opis: 'Fantastični roman iz poznatog Witcher serijala.',
    slika: 'https://m.media-amazon.com/images/I/81rcURiyM2L._AC_UF1000,1000_QL80_.jpg'
  },
  {
    id: 2,
    naslov: 'Gospodar prstenova: Prstenova družina',
    autor: 'J.R.R. Tolkien',
    opis: 'Prvi dio epske trilogije o borbi protiv Saurona.',
    slika: 'https://upload.wikimedia.org/wikipedia/en/8/8e/The_Fellowship_of_the_Ring_cover.gif'
  },
  {
    id: 3,
    naslov: 'The Name of the Wind',
    autor: 'Patrick Rothfuss',
    opis: 'Priča o Kvotheu, talentiranom mladom čarobnjaku i glazbeniku.',
    slika: 'https://m.media-amazon.com/images/S/compressed.photo.goodreads.com/books/1704917687i/186074.jpg'
  },
  {
    id: 4,
    naslov: 'Mistborn: The Final Empire',
    autor: 'Brandon Sanderson',
    opis: 'Prvi dio Mistborn serijala, epska fantazija o pobuni protiv tiranskog vladara.',
    slika: 'https://m.media-amazon.com/images/I/811qBmIYTFL._AC_UF1000,1000_QL80_.jpg'
  },
  {
    id: 5,
    naslov: 'The Lies of Locke Lamora',
    autor: 'Scott Lynch',
    opis: 'Priča o genijalnom lopovu i njegovoj bandi u fantastičnom gradu Camorr.',
    slika: 'https://www.menartshop.hr/wp-content/uploads/2025/04/b595b1b1-9cdb-4245-8a4a-fbc0ca9fda6b.png'
  },
  {
    id: 6,
    naslov: 'Eragon',
    autor: 'Christopher Paolini',
    opis: 'Prva knjiga iz Inheritance Cycle serijala, avantura mladog jahača zmaja.',
    slika: 'https://upload.wikimedia.org/wikipedia/en/c/ce/Eragon_book_cover.png'
  },
  {
    id: 7,
    naslov: 'The Hobbit',
    autor: 'J.R.R. Tolkien',
    opis: 'Avanture Bilba Bagginsa i putovanje kroz Srednju Zemlju.',
    slika: 'https://m.media-amazon.com/images/I/71jD4jMityL._AC_UF1000,1000_QL80_.jpg'
  }
])

const searchQuery = ref('')

const searchBy = ref('naslov')

const searchOptions = [
  { label: 'Po naslovu', value: 'naslov' },
  { label: 'Po autoru', value: 'autor' }
]

const columns = [
  { 
    name: 'id', 
    label: 'ID', 
    field: 'id', 
    align: 'left' 
  },
  { 
    name: 'slika', 
    label: 'Slika', 
    field: 'slika', 
    align: 'left' 
  },
  { 
    name: 'naslov', 
    label: 'Naslov', 
    field: 'naslov', 
    align: 'left' 
  },
  { 
    name: 'autor', 
    label: 'Autor', 
    field: 'autor', 
    align: 'left' 
  }
]

const filteredBooks = ref([...rows.value])

function searchBooks() {
  const query = searchQuery.value.toLowerCase()
  if (!query) {
    filteredBooks.value = [...rows.value]
    return
  }

  filteredBooks.value = rows.value.filter(book => {
    return book[searchBy.value].toLowerCase().includes(query)
  })
}
</script>