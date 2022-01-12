<template>
    <div class="footer" >
        <v-row>
            <v-col col="12">
                <v-footer color="brown" padless >
                    <v-card flat tile class="brown white--text text-center mx-auto">
                        <v-card-text>
                            <v-btn v-for="icon in icons" :key="icon" class="mx-4 white--text" icon>
                                <v-icon size="24px">{{ icon }}</v-icon>
                            </v-btn>
                        </v-card-text>
                        <v-card-text class="white--text pt-0 pie">
                            <p><v-icon>mdi-phone</v-icon>999 99 99 99</p>
                            <p><v-icon>mdi-map-marker</v-icon>Carretera de los Jabalíes, salida 524</p>
                        </v-card-text>
                        <v-divider></v-divider>
                        <v-card-text class="white--text pie"><strong>— RESERVA NATURAL —</strong></v-card-text>
                    </v-card>
                </v-footer>
            </v-col>
        </v-row>
    </div>
</template>

<script>
  export default {
    data: () => ({
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
    }),
  }
</script> 


<style scoped>
    .pie{
        font-size: 130%;
    }
</style>