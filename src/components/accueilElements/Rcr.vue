<template>
  <v-container>
    <v-select :items="optionsRcr" :item-text="getOptionsRcr.text" :item-value="getOptionsRcr.id" label="et/ou/sauf" outlined v-model="getOptionsRcrDefaultSelected.text"></v-select>
    <v-combobox clearable multiple outlined small-chips label="Saisir le rcr d'une bibliothèque" placeholder="rcr à saisir"></v-combobox>
    <v-select :items="optionsLotRcr" :item-text="getOptionsLotRcr.text" :item-value="getOptionsLotRcr.id" label="Pour ce lot de RCR" outlined v-model="getOptionsLotRcrDefaultSelected.text"></v-select>
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
    private optionsRcrDefaultSelected: Array<Provider> = [
      {id: 1, key:"optionRcrOU", text: "OU" }
    ];
    private optionsLotRcrDefaultSelected: Array<Provider> = [
      {id: 1, key:"optionLotRcrOU", text: "OU" }
    ];
    private optionsRcr: Array<Provider> = [
      {id:0,key:"optionRcrET", text:"ET"},
      {id:1,key:"optionRcrOU", text:"OU"},
      {id:2,key:"optionRcrSAUF", text:"SAUF"}
    ];
    private optionsLotRcr: Array<Provider> = [
      {id:0,key:"optionLotRcrET",text:"ET"},
      {id:1,key:"optionLotRcrOU",text:"OU"},
    ];
  public getOptionsRcrDefaultSelected(numberId: number): string {
    return this.optionsRcrDefaultSelected[numberId].text;
  }
  public getOptionsLotRcrDefaultSelected(numberId: number): string {
    return this.optionsLotRcrDefaultSelected[numberId].text;
  }
  public getOptionsRcr(numberId: number): string {
    return this.optionsRcr[numberId].text;
  }
  public getOptionsLotRcr(numberId: number): string {
    return this.optionsLotRcr[numberId].text;
  }
}
</script>
