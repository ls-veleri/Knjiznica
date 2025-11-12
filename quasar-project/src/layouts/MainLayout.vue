<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>Knjižnica</q-toolbar-title>
        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>Izbornik</q-item-label>
        <EssentialLink v-for="link in linksList" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view :key="$route.fullPath" />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Naslovnica',
    caption: 'Početna stranica',
    icon: 'home',
    link: '/',
  },
  {
    title: 'Nove knjige',
    caption: 'Pregled novih knjiga',
    icon: 'auto_stories',
    link: '/noveknjige',
  },
  {
    title: 'Popis svih knjiga',
    caption: 'Sve knjige u knjižnici',
    icon: 'menu_book',
    link: '/popisknjiga',
  },
  {
    title: 'Pretraživanje',
    caption: 'Pretraži knjige po nazivu ili autoru',
    icon: 'search',
    link: '/pretrazivanje',
  },
  {
    title: 'Unos nove knjige',
    caption: 'Dodaj novu knjigu u knjižnicu',
    icon: 'add_box',
    link: '/unosknjige',
  },
  {
    title: 'Lokacija',
    caption: 'Gdje se nalazi knjižnica',
    icon: 'place',
    link: '/lokacija',
  },
  {
    title: 'Login',
    caption: 'Prijava korisnika',
    icon: 'login',
    link: '/login',
  },
  {
    title: 'Registracija',
    caption: 'Kreiraj novi račun',
    icon: 'person_add',
    link: '/registracija',
  },
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>