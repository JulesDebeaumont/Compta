<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>

        <q-toolbar-title>
          La compta, c'est maintenant.
        </q-toolbar-title>

        <q-btn>
          <q-item-section>
            <q-item-label>À propos</q-item-label>
          </q-item-section>
        </q-btn>

      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">

</script>
