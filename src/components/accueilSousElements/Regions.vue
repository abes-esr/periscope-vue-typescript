<template>
   <v-container>
      <v-row :justify="getHorizontalJustifyValue(1)" style="background-color: #e6e6e6">
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-on:click="changeValueOneCheckboxElement(prop_regions[m - 1])" v-for="m in 5" :key="m" :value="prop_regions[m - 1].value" :label="prop_regions[m - 1].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-on:click="changeValueOneCheckboxElement(prop_regions[m + 4])" v-for="m in 5" :key="m" :value="prop_regions[m + 4].value" :label="prop_regions[m + 4].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-on:click="changeValueOneCheckboxElement(prop_regions[m + 9])" v-for="m in 6" :key="m" :value="prop_regions[m + 9].value" :label="prop_regions[m + 9].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-on:click="changeValueOneCheckboxElement(prop_regions[m + 15])" v-for="m in 6" :key="m" :value="prop_regions[m + 15].value" :label="prop_regions[m + 15].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col>
            <p>{{ prop_regions }}</p>
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
export default class Regions extends Mixins(GlobalPropertiesMixin) {
   @Prop({required: true}) prop_regions: Array<Provider>;

   private changeValueOneCheckboxElement(element: Provider): void {
      element.value = !element.value;
   }
}
</script>
