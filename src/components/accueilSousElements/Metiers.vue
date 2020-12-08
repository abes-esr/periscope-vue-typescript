<template>
   <v-container>
      <v-row :justify="getHorizontalJustifyValue(1)" style="background-color: #e2e4ff">
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-for="m in 4" :key="m" :value="prop_metiers[m - 1].id" :label="prop_metiers[m - 1].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-for="m in 4" :key="m" :value="prop_metiers[m + 3].id" :label="prop_metiers[m + 3].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-for="m in 4" :key="m" :value="prop_metiers[m + 7].id" :label="prop_metiers[m + 7].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-for="m in 5" :key="m" :value="prop_metiers[m + 11].id" :label="prop_metiers[m + 11].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
      </v-row>
   </v-container>
</template>

<script lang="ts">
import {Component, Prop, Mixins} from 'vue-property-decorator';
import GlobalPropertiesMixin from '@/mixins/globalProperties';

interface Provider {
   id: number;
   key: string;
   text: string;
   value: boolean;
}

@Component
export default class Metiers extends Mixins(GlobalPropertiesMixin) {

   @Prop({required: true}) prop_metiers: Array<Provider>;
}
</script>
