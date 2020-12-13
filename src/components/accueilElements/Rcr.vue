<template>
   <v-container>
      <v-select v-on:click="disableDefaultSlotValue0 = false" :items="optionsRcr" outlined v-model="optionsRcrSelected">
         <template v-if="disableDefaultSlotValue0" slot="selection">
            <span style="color: grey">Et/ou/sauf</span>
         </template>
      </v-select>
      <p>{{ optionsRcrSelected }}</p>
      <v-combobox clearable multiple outlined small-chips label="Saisir le rcr d'une bibliothèque" placeholder="rcr à saisir" v-model="rcrHandler"></v-combobox>
      <p>{{ rcrHandler }}</p>
      <v-select v-on:click="disableDefaultSlotValue1 = false" :items="optionsLotRcr" outlined v-model="optionsLotRcrSelected">
         <template v-if="disableDefaultSlotValue1" slot="selection">
            <span style="color: grey">Ou/Et</span>
         </template>
      </v-select>
      <p>{{ optionsLotRcrSelected }}</p>
   </v-container>
</template>

<script lang="ts">
import {Component, Vue, Watch} from 'vue-property-decorator';

interface Provider {
   id: number;
   key: string;
   text: string;
   value: Ensemble;
}

interface RcrProvider {
   id: number;
   value: number;
}

enum Ensemble {
   Union, //0
   Intersection, //1
   Difference, //2
}

@Component
export default class VuePpn extends Vue {
   private disableDefaultSlotValue0 = true;
   private disableDefaultSlotValue1 = true;

   private optionsRcr: Array<Provider> = [
      {id: 0, key: 'optionRcrET', text: 'ET', value: Ensemble.Union},
      {id: 1, key: 'optionRcrOU', text: 'OU', value: Ensemble.Intersection},
      {id: 2, key: 'optionRcrSAUF', text: 'SAUF', value: Ensemble.Difference},
   ];
   private optionsRcrSelected: Ensemble = Ensemble.Intersection;

   private rcrHandler: Array<RcrProvider> = [];

   @Watch('rcrHandler')
   rcrTyped(newVal: Array<RcrProvider>) {
      newVal.forEach(element => console.log(element))
   }

   private optionsLotRcr: Array<Provider> = [
      {id: 0, key: 'optionLotRcrET', text: 'ET', value: Ensemble.Union},
      {id: 1, key: 'optionLotRcrOU', text: 'OU', value: Ensemble.Intersection},
   ];
   private optionsLotRcrSelected: Ensemble = Ensemble.Intersection;

   public changeValueOfEnumElement(text: string, enumElement: Ensemble): void {
      switch (text) {
         case 'ET':
            enumElement = Ensemble.Union;
            break;
         case 'OU':
            enumElement = Ensemble.Intersection;
            break;
         case 'SAUF':
            enumElement = Ensemble.Difference;
            break;
         default:
            enumElement = Ensemble.Union;
            break;
      }
   }

}
</script>
