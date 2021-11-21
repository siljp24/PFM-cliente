<template>
    <div class="layout-historia-animal">
        <v-app>
            <AppBar2 />
            <v-main>
                <v-container>
                    <v-row class="mt-10">
                        <v-col cols="2">
                            <v-btn v-on:click="diario" block color="deep-orange lighten-3">DIARIO</v-btn>
                        </v-col>
                    </v-row>
                    <v-row class="mt-10">
                        <v-col class="mt-10">
                            <Nuxt />
                        </v-col>
                    </v-row>
                </v-container>
            </v-main>
        </v-app>
    </div>
</template>

<script>
export default {
   methods:{
       diario(){
           this.$router.push('/voluntario/idAnimal')
       }
   }
}
</script>