<template>
   <v-container>
      <v-select dense label="Par defaut, ou" v-on:click="disableDefaultSlotValue0 = false" :items="optionsRcr" outlined v-model="optionsRcrSelected">
         <template v-if="disableDefaultSlotValue0" slot="selection">
            <span style="color: grey">Et/ou/sauf</span>
         </template>
      </v-select>
      <p>{{ optionsRcrSelected }}</p>
      <v-combobox clearable multiple outlined small-chips label="Saisir le rcr d'une bibliothèque" style='background-color: white; max-height: 3.5em' placeholder="rcr à saisir" v-model="rcrArrayTyped"></v-combobox>
      <p>{{ rcrHandler }}</p>
      <v-select dense label="Pour ce lot de rcr (par defaut, ou)" v-on:click="disableDefaultSlotValue1 = false" :items="optionsLotRcr" outlined v-model="optionsLotRcrSelected">
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

   private rcrArrayTyped = [];
   private rcrHandler: Array<RcrProvider> = [];

   /**
    * The global array of combobox component watched by this function, after each typed by user, this function
    * is launched to observe the final current array in combobox
    * @param newArrayVal
    */
   @Watch('rcrArrayTyped')
   rcrTyped(newArrayVal: []): void {
      if (newArrayVal.length === 0) {
         this.rcrHandler = [];
         return;
      }

      //if the value of last element of array contains characters, it removes from list, return = get out of function
      if (new RegExp('\\D').test(newArrayVal[newArrayVal.length - 1])) {
         newArrayVal.pop();
         return;
      }

      //if the value of last element of array contains only digits, and array target to fill length is different from current Array watched
      if (new RegExp('\\d').test(newArrayVal[newArrayVal.length - 1]) && this.rcrHandler.length !== newArrayVal.length) {
         //conversion of string input (who contains only digits) in number type
         let newLastValConvertedInNumberType: number = +newArrayVal[newArrayVal.length - 1];
         //push element in rcrHandler array, with id value associated at rcr
         console.log(this.rcrHandler.length !== newArrayVal.length);
         this.rcrHandler.push(
            new (class implements RcrProvider {
               id: number = newArrayVal.length - 1;
               value: number = newLastValConvertedInNumberType;
            })()
         );
      }
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
