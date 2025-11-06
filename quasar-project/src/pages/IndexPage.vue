<template>
  <q-page class="bg-grey-1 q-pa-none">

    <div class="relative w-full flex flex-center hero-container">
      <img
        alt="Knjižnica"
        src="~assets/knjiznica.jpg"
        class="hero-image"
      />
      <div class="absolute-bottom text-white text-center q-pa-md overlay-text">
        <h1 class="text-h4 text-weight-bold">Dobrodošli u Knjižnicu!</h1>
        <p class="text-subtitle2">
          Vaše mjesto za čitanje, znanje i istraživanje novih svjetova.
        </p>
      </div>
    </div>

    <div class="q-pa-lg text-center" style="max-width: 600px; margin: 0 auto;">
      <p class="text-body1 q-mb-md">
        Naša knjižnica nudi velik izbor knjiga, novih naslova i klasika svih žanrova.
        Ovdje možete pregledavati popis svih knjiga, otkrivati nove naslove,
        pretraživati autore i pronaći nas na karti.
      </p>

      <q-btn
        label="Pretraži knjige"
        color="primary"
        to="/pretrazivanje"
        class="q-mt-md"
        icon="search"
        unelevated
      />
    </div>

  </q-page>
</template>

<script setup>
</script>

<style scoped>
.q-page {
  min-height: 100vh;
  padding: 0;
  margin: 0;
}

.hero-container {
  margin-top: 0;
}

.hero-image {
  width: 100%;
  max-height: 280px;
  object-fit: cover;
  display: block;
}

.overlay-text {
  background: rgba(0, 0, 0, 0.4);
}
</style>