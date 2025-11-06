<template>
  <q-page padding class="q-pa-md">

    <div class="q-gutter-md" style="max-width: 400px;">

      <q-input
        v-model="korisnickoIme"
        label="Korisničko ime"
        outlined
        clearable
      />

      <q-input
        v-model="lozinka"
        label="Lozinka"
        type="password"
        outlined
        clearable
      />

      <q-btn
        label="Potvrdi"
        color="primary"
        class="full-width"
        @click="prijavaKorisnika"
      />

    </div>

  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const korisnickoIme = ref('')
const lozinka = ref('')

function prijavaKorisnika() {
  if (!korisnickoIme.value || !lozinka.value) {
    alert('Molimo unesite korisničko ime i lozinku')
    return
  }

  const loginPodaci = {
    korisnicko_ime: korisnickoIme.value,
    lozinka: lozinka.value
  }

  console.log('Login podaci:', loginPodaci)
  alert('Prijava uspješna (test)')
  
  korisnickoIme.value = ''
  lozinka.value = ''
}
</script>