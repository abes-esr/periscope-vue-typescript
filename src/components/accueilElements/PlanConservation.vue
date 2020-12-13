<template>
   <v-container class="outlined-app">
      <v-row no-gutters>
         <v-col>
            <h2 v-html="title"></h2>
         </v-col>
      </v-row>
      <v-row :align="getVerticalAlignValue(1)" :justify="getHorizontalJustifyValue(2)" class="ma-0 pa-0" dense>
         <v-col v-for="iteration in this.choixTousOuAucun" v-bind:key="iteration.id" xs="6" sm="1" align-self="end" class="ma-0 pa-0">
            <v-btn small depressed color="primary" v-on:click="changeAllValuesWhenClicked(iteration.text)" v-html="iteration.text"></v-btn>
         </v-col>
      </v-row>
      <v-row>
         <component-regions v-bind:prop_regions="regions"></component-regions>
      </v-row>
      <v-row>
         <component-metiers v-bind:prop_metiers="metiers"></component-metiers>
      </v-row>
   </v-container>
</template>

<script lang="ts">
import {Component, Mixins} from 'vue-property-decorator';
import GlobalPropertiesMixin from '@/mixins/globalProperties.ts';
import ComponentRegions from '@/components/accueilSousElements/Regions.vue';
import ComponentMetiers from '@/components/accueilSousElements/Metiers.vue';

interface Provider {
   id: number;
   key: string;
   text: string;
   value: boolean;
}

@Component({
   components: {
      ComponentRegions,
      ComponentMetiers,
   },
})
export default class PlanConservation extends Mixins(GlobalPropertiesMixin) {
   private regions: Array<Provider> = [
      {id: 0, key: 'Aq', text: 'Aquitaine', value: false},
      {id: 1, key: 'Au', text: 'Auvergne', value: false},
      {id: 2, key: 'Bo', text: 'Bourgogne', value: false},
      {id: 3, key: 'Br', text: 'Bretagne', value: false},
      {id: 4, key: 'Ca', text: 'Champagne-Ardenne', value: false},
      {id: 5, key: 'Cap', text: 'Champagne-Ardenne Picardie', value: false},
      {id: 6, key: 'Co', text: 'Corse', value: false},
      {id: 7, key: 'Fc', text: 'Franche-Comté', value: false},
      {id: 8, key: 'Lr', text: 'Languedoc-Roussillon', value: false},
      {id: 9, key: 'Li', text: 'Limousin', value: false},
      {id: 10, key: 'Lo', text: 'Lorraine', value: false},
      {id: 11, key: 'Mp', text: 'Midi-Pyrénées', value: false},
      {id: 12, key: 'Npc', text: 'Nord-Pas-de-Calais', value: false},
      {id: 13, key: 'Pca', text: 'PACA', value: false},
      {id: 14, key: 'Pc', text: 'Poitou-Charentes', value: false},
      {id: 15, key: 'Pdl', text: 'Pays de Loire', value: false},
      {id: 16, key: 'Pi', text: 'Picardie', value: false},
      {id: 17, key: 'Ra', text: 'Rhône-Alpes', value: false},
      {id: 18, key: 'Sam', text: 'Sciences Aix-Marseille', value: false},
      {id: 19, key: 'Scvdl', text: 'Sciences Centre Val de Loire', value: false},
      {id: 20, key: 'Udp', text: 'Université de Poitiers', value: false},
      {id: 21, key: 'Udr', text: 'Université de Rouen', value: false},
   ];
   private metiers: Array<Provider> = [
      {id: 0, key: 'Aem', text: 'Arts-et-Métiers', value: false},
      {id: 1, key: 'Ads', text: 'Arts du spectacle', value: false},
      {id: 2, key: 'Saa', text: "Sciences de l'Antiquité et Archéologie", value: false},
      {id: 3, key: 'Ch', text: 'Chimie', value: false},
      {id: 4, key: 'Dr', text: 'Droit', value: false},
      {id: 5, key: 'Ebco', text: 'Europe balkanique, centrale et orientale', value: false},
      {id: 6, key: 'Llcg', text: 'Langues, littératures, civilisation germaniques', value: false},
      {id: 7, key: 'Ge', text: 'Géographie', value: false},
      {id: 8, key: 'Ei', text: 'Etudes italiennes', value: false},
      {id: 9, key: 'Me', text: 'Médiéval', value: false},
      {id: 10, key: 'Sdn', text: 'Sciences du Numériques', value: false},
      {id: 11, key: 'Mr', text: 'Mathématiques RNBM', value: false},
      {id: 12, key: 'Mede', text: 'Médecine', value: false},
      {id: 13, key: 'Pp', text: 'Psychologie, Psychanalyse', value: false},
      {id: 14, key: 'St', text: 'STAPS', value: false},
      {id: 15, key: 'Phi', text: 'Philosophie', value: false},
      {id: 16, key: 'Phy', text: 'Physique', value: false},
   ];
   private choixTousOuAucun: Array<Provider> = [
      {id: 0, key: '', value: false, text: 'Tous'},
      {id: 1, key: '', value: false, text: 'Aucun'},
   ];

   private title = 'Choisir un plan de conservation';

   /**
    * Méthode changeant l'ensemble des valeurs d'un tableau donné
    * @param arrayMember tableau passé en paramètre
    * @param booleanValue valeur du booléen d'un élément du tableau
    * @private
    */
   private arrayChangeAllBooleanValues(arrayMember: Array<Provider>, booleanValue: boolean): void {
      arrayMember.forEach((element) => (element.value = booleanValue));
   }

   /**
    * Méthode changeant les valeurs des éléments au moment d'un clic
    * @param localText valeur d'un élement passé dans l'iteration du template
    * @private
    */
   private changeAllValuesWhenClicked(localText: string): void {
      switch (localText) {
         case 'Tous':
            this.arrayChangeAllBooleanValues(this.regions, true);
            this.arrayChangeAllBooleanValues(this.metiers, true);
            break;
         case 'Aucun':
            this.arrayChangeAllBooleanValues(this.regions, false);
            this.arrayChangeAllBooleanValues(this.metiers, false);
            break;
         default:
            break;
      }
   }
}
</script>
