<template>
   <v-container>
      <v-row :justify="getHorizontalJustifyValue(1)" style="background-color: #e6e6e6">
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-for="m in 5" :key="m" :value="prop_regions[m - 1].id" :label="prop_regions[m - 1].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-for="m in 5" :key="m" :value="prop_regions[m + 4].id" :label="prop_regions[m + 4].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-for="m in 6" :key="m" :value="prop_regions[m + 8].id" :label="prop_regions[m + 8].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
         </v-col>
         <v-col xs="6" sm="3" class="margin-v-col-accueil">
            <v-checkbox v-for="m in 6" :key="m" :value="prop_regions[m + 13].id" :label="prop_regions[m + 13].text" hide-details class="margin-v-checkbox-accueil"></v-checkbox>
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
}
</script>
