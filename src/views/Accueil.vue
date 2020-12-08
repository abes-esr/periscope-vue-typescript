<template>
   <v-container>
      <component-header></component-header>
      <component-recherche></component-recherche>
      <component-footer></component-footer>
   </v-container>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';
import ComponentHeader from '@/components/accueil/Header.vue';
import ComponentRecherche from '@/components/accueil/Recherche.vue';
import ComponentFooter from '@/components/accueil/Footer.vue';

@Component({
   components: {
      ComponentHeader,
      ComponentRecherche,
      ComponentFooter,
   },
})
//La vue importe les composants avec l'annotation @Component en tableau, mais ne s'exporte pas en composant
export default class Accueil extends Vue {}
</script>
