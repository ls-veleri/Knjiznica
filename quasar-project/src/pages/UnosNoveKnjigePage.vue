<template>
  <q-page padding class="bg-grey-1">
    <h4 class="text-h5 text-primary text-center q-mb-md">
      Unos nove knjige
    </h4>

    <div class="q-pa-md q-gutter-md" style="max-width: 600px; margin: 0 auto;">
      <q-card 
        flat 
        bordered 
        class="q-pa-md"
      >
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
          :multiple="false" 
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
      <h6 class="text-subtitle1 q-mb-sm text-center">Spremljene knjige:</h6>

      <div class="row q-gutter-md justify-center">
        <q-card 
          v-for="k in knjige" 
          :key="k.id" 
          class="my-card" 
          bordered 
          flat 
          style="width: 300px;"
        >
          <q-img 
            v-if="k.slika" 
            :src="getSlika(k.slika)" 
            alt="Slika knjige" 
            class="book-cover"
          />

          <q-card-section>
            <div class="text-h6">{{ k.naslov }}</div>
            <div class="text-subtitle2">Autor: {{ k.autor }}</div>
            <div class="text-caption text-grey q-mt-xs">{{ k.status }}</div>
          </q-card-section>

          <q-separator inset />

          <q-card-section class="q-pt-none">
            {{ k.opis }}
          </q-card-section>
        </q-card>
      </div>
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

function getSlika(file) {
  if (!file) return ''
  if (Array.isArray(file)) file = file[0]
  return typeof file === 'string' ? file : URL.createObjectURL(file)
}
</script>

<style scoped>
.my-card {
  transition: 0.3s;
}
.my-card:hover {
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
}
.book-cover {
  width: 100%;
  height: 450px;
  object-fit: cover;
  border-bottom: 1px solid rgba(0,0,0,0.1);
  border-radius: 8px 8px 0 0;
}
</style>