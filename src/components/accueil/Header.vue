<template>
  <v-container class="ma-0 pa-0">
    <v-row style="max-height: 6em" :align="getAlignmentValue(1)" justify="center" no-gutters :style="getHeightsCssValue(0)">
      <v-col xs="12" sm="12">
        <img src="@/assets/periscope.png" :style="autoResizeImage" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Component, Mixins } from "vue-property-decorator";
import GlobalPropertiesMixin from "@/mixins/globalProperties";

//Le composant utilise l'annotation composant juste avant l'export de la classe
@Component
export default class Header extends Mixins(GlobalPropertiesMixin) {}
</script>
