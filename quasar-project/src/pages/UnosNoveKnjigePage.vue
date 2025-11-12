<template>
  <q-page padding class="bg-grey-1">
    <h4 class="text-h5 text-center q-mb-md">Unos nove knjige</h4>

    <div class="q-pa-md q-gutter-md" style="max-width: 600px; margin: 0 auto;">
      <q-card flat bordered class="q-pa-md">

        <q-input 
          filled 
          v-model="id" 
          label="ID knjige" 
          readonly 
          class="q-mb-md"
        />

        <q-input 
          filled 
          v-model="naslov" 
          label="Naslov knjige" 
          class="q-mb-md"
        />

        <q-input 
          filled 
          v-model="autor" 
          label="Autor" 
          class="q-mb-md"
        />

        <q-input 
          filled 
          type="textarea" 
          v-model="opis" 
          label="Opis" 
          class="q-mb-md"
        />

        <q-file 
          filled 
          v-model="slika" 
          label="Odaberi sliku" 
          accept="image/*" 
          class="q-mb-md"
        />

        <q-select 
          filled 
          v-model="status" 
          :options="['Slobodna', 'Zauzeta']" 
          label="Status knjige" 
          class="q-mb-md"
        />

        <div class="row q-gutter-sm justify-center q-mt-md">
          <q-btn 
            label="Spremi" 
            color="primary" 
            icon="save" 
            unelevated
            @click="spremiKnjigu" 
          />
          <q-btn 
            label="Odustani" 
            color="negative" 
            flat 
            icon="cancel" 
            @click="odustani" 
          />
        </div>

      </q-card>
    </div>

    <div v-if="knjige.length" class="q-pa-md">
      <h6 class="text-subtitle1 q-mb-sm">Spremljene knjige:</h6>
      <ul>
        <li v-for="k in knjige" :key="k.id">
          {{ k.id }} - {{ k.naslov }} ({{ k.autor }}) — {{ k.status }}
        </li>
      </ul>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const knjige = ref([])
const id = ref(1)
const naslov = ref('')
const autor = ref('')
const opis = ref('')
const slika = ref(null)
const status = ref('Slobodna')

function spremiKnjigu() {
  knjige.value.push({
    id: id.value,
    naslov: naslov.value,
    autor: autor.value,
    opis: opis.value,
    slika: slika.value,
    status: status.value
  })
  id.value++
  odustani()
}

function odustani() {
  naslov.value = ''
  autor.value = ''
  opis.value = ''
  slika.value = null
  status.value = 'Slobodna'
}
</script>