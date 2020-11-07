<template>
  <v-container>
    <v-carousel
    cycle
    height="400"
    hide-delimiter-background
    show-arrows-on-hover
  >
    <v-carousel-item
      v-for="(slide, i) in slides"
      :key="i"
    >
      <v-sheet
        :color="colors[i]"
        height="100%"
      >
        <v-row
          class="fill-height"
          align="center"
          justify="center"
        >
          <div class="display-4">
            {{ slide }} 
          </div>
        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
  </v-container>
</template>

<script>
/**
 * @copyright carlosramirezdev@gmail.com todos los derechos reservados
 * @author carlosr.dev
 * @description Seccion Home
 */

export default {
  name: 'Home',
  components: {
   //
  },
  data() {
    return {
      colors: [
          'green',
          'info'
        ],
        slides: [
          'Vue Js',
          'Vuetify'
        ],
    }
  },
}
</script>
