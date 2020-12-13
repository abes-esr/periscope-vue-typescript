<template>
   <v-container class="outlined-app" style="background-color: #f8f9f9">
      <v-container class="ma-0 pa-0">
         <v-row :align="getVerticalAlignValue(1)" :justify="getHorizontalJustifyValue(1)" no-gutters>
            <v-col class="outlined-app" style="background-color: #0f75bc">
               <h2 v-html="title" style="color: white"></h2>
            </v-col>
         </v-row>
      </v-container>
      <v-container>
         <component-plan-de-conservation></component-plan-de-conservation>
      </v-container>
      <v-container>
         <v-row>
            <v-col>
               <component-rcr class="outlined-app"></component-rcr>
            </v-col>
            <v-col>
               <component-ppn class="outlined-app"></component-ppn>
            </v-col>
         </v-row>
      </v-container>
      <v-container>
         <component-boutons-recherche></component-boutons-recherche>
      </v-container>
   </v-container>
</template>
<script lang="ts">
import {Component, Mixins} from 'vue-property-decorator';
import GlobalPropertiesMixin from '@/mixins/globalProperties';
import ComponentPpn from '@/components/accueilElements/Ppn.vue';
import ComponentRcr from '@/components/accueilElements/Rcr.vue';
import ComponentBoutonsRecherche from '@/components/accueilElements/BoutonsRecherche.vue';
import ComponentPlanDeConservation from '@/components/accueilElements/PlanConservation.vue';

@Component({
   components: {
      ComponentPpn,
      ComponentRcr,
      ComponentBoutonsRecherche,
      ComponentPlanDeConservation,
   },
})
export default class Recherche extends Mixins(GlobalPropertiesMixin) {
   private title = 'Recherche';
}
</script>
