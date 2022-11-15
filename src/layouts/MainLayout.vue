<template>
  <q-layout view="lHh Lpr lFf" class="bg-grey-10">
    <q-header elevated>
      <q-toolbar>

        <q-toolbar-title>
          La compta, c'est maintenant.
        </q-toolbar-title>

        <q-btn :to="{ name: 'about' }" @click="about = true">
          <q-item-section>
            <q-item-label>À propos</q-item-label>
          </q-item-section>
        </q-btn>

        <q-dialog v-model="about">
          <q-card class="bg-grey-10">
            <q-card-section>
              <div class="text-h6">À propos</div>
            </q-card-section>

            <q-card-section class="q-pt-none">
              Créer par Jules Debeaumont OST™<br />
              Dernière màj le 15/11/2022
            </q-card-section>

            <q-card-actions align="between">
              <a target="_blank" href="https://github.com/JulesDebeaumont/Compta">
                <q-btn flat label="GitHub" color="primary" />
              </a>
              <q-btn flat label="Fermer" color="primary" v-close-popup />
            </q-card-actions>
          </q-card>
        </q-dialog>

      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';

// refs
const about = ref(false)

</script>
