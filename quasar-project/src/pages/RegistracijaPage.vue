<template>
  <q-page padding class="q-pa-md">

    <div class="q-gutter-md" style="max-width: 400px;">

      <q-input
        v-model="ime"
        label="Ime"
        outlined
        clearable
      />

      <q-input
        v-model="prezime"
        label="Prezime"
        outlined
        clearable
      />

      <q-input
        v-model="email"
        label="Email"
        type="email"
        outlined
        clearable
      />

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
        @click="registrirajKorisnika"
        class="full-width"
      />

    </div>

  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const ime = ref('')
const prezime = ref('')
const email = ref('')
const korisnickoIme = ref('')
const lozinka = ref('')

function registrirajKorisnika() {
  if (!ime.value || !prezime.value || !email.value || !korisnickoIme.value || !lozinka.value) {
    alert('Molimo popunite sva polja')
    return
  }

  const noviKorisnik = {
    ime: ime.value,
    prezime: prezime.value,
    email: email.value,
    korisnicko_ime: korisnickoIme.value,
    lozinka: lozinka.value
  }

  console.log('Registriran korisnik:', noviKorisnik)
  alert('Registracija uspješna!')

  ime.value = ''
  prezime.value = ''
  email.value = ''
  korisnickoIme.value = ''
  lozinka.value = ''
}
</script>