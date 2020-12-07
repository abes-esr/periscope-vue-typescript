<template>
   <v-container>
      <v-select :items="optionsPpn" :item-text="getOptionsPpn.text" :item-value="optionsPpn.id" label="et/ou/sauf" outlined v-model="getOptionsPPnDefaultSelected.text"></v-select>
      <v-row>
         <v-col>
            <v-text-field dense clearable multiple outlined small-chips label="PPN" placeholder=" "></v-text-field>
         </v-col>
         <v-col>
            <v-text-field dense clearable multiple outlined small-chips label="ISSN" placeholder=" "></v-text-field>
         </v-col>
      </v-row>
      <v-expansion-panels flat class="outlined-app">
         <v-expansion-panel>
            <v-expansion-panel-header>
               Rechercher par d'autres critères
            </v-expansion-panel-header>
            <v-expansion-panel-content>
               <v-text-field clearable multiple outlined small-chips label="Mots du titre" placeholder=" "></v-text-field>
               <span>
                  <v-select :items="optionsEditor" :item-text="optionsEditor.text" :item-value="optionsEditor.id" label="et/ou/sauf" outlined v-model="getOptionsEditorDefaultSelected.text"></v-select>
                  <v-text-field outlined label="Editeur" placeholder=" "></v-text-field>
               </span>
               <span>
                  <v-select :items="optionsLanguage" :item-text="optionsEditor.text" :item-value="optionsEditor.id" label="et/ou/sauf" outlined v-model="getOptionsLanguageDefaultSelected.text"></v-select>
                  <v-text-field outlined label="Langue du document" placeholder=" "></v-text-field>
               </span>
               <span>
                  <v-select :items="optionsCountry" :item-text="optionsEditor.text" :item-value="optionsEditor.id" label="et/ou/sauf" outlined v-model="getOptionsCountryDefaultSelected.text"></v-select>
                  <v-text-field outlined label="Pays de publication" placeholder=" "></v-text-field>
               </span>
            </v-expansion-panel-content>
         </v-expansion-panel>
      </v-expansion-panels>
   </v-container>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';

interface Provider {
   id: number;
   key: string;
   text: string;
}

@Component
export default class VuePpn extends Vue {
   private optionsPpnDefaultSelected: Array<Provider> = [{id: 1, key: 'optionRcrOU', text: 'OU'}];

   private optionsEditorDefaultSelected: Array<Provider> = [{id: 1, key: 'optionEditor', text: 'ET'}];

   private optionsLanguageDefaultSelected: Array<Provider> = [{id: 1, key: 'optionLanguage', text: 'ET'}];

   private optionsCountryDefaultSelected: Array<Provider> = [{id: 1, key: 'optionCountry', text: 'ET'}];

   private optionsPpn: Array<Provider> = [
      {id: 0, key: 'optionPpnET', text: 'ET'},
      {id: 1, key: 'optionPpnOU', text: 'OU'},
      {id: 2, key: 'optionPpnSAUF', text: 'SAUF'},
   ];
   private optionsEditor: Array<Provider> = [
      {id: 0, key: 'optionEditorET', text: 'ET'},
      {id: 1, key: 'optionEditorOU', text: 'OU'},
      {id: 2, key: 'optionEditorSAUF', text: 'SAUF'},
   ];
   private optionsLanguage: Array<Provider> = [
      {id: 0, key: 'optionLanguage', text: 'ET'},
      {id: 1, key: 'optionLanguage', text: 'OU'},
      {id: 2, key: 'optionLanguageSAUF', text: 'SAUF'},
   ];
   private optionsCountry: Array<Provider> = [
      {id: 0, key: 'optionCountryET', text: 'ET'},
      {id: 1, key: 'optionCountryOU', text: 'OU'},
      {id: 2, key: 'optionCountrySAUF', text: 'SAUF'},
   ];

   public getTextFromIdForArray(arrayTarget: Array<Provider>, numberId: number): string {
      return arrayTarget[numberId].text;
   }

   public getOptionsPPnDefaultSelected(numberId: number): string {
      return this.optionsPpnDefaultSelected[numberId].text;
   }
   public getOptionsEditorDefaultSelected(numberId: number): string {
      return this.optionsEditorDefaultSelected[numberId].text;
   }
   public getOptionsLanguageDefaultSelected(numberId: number): string {
      return this.optionsLanguageDefaultSelected[numberId].text;
   }
   public getOptionsCountryDefaultSelected(numberId: number): string {
      return this.optionsCountryDefaultSelected[numberId].text;
   }
   public getOptionsPpn(numberId: number): string {
      return this.optionsPpn[numberId].text;
   }
}
</script>
