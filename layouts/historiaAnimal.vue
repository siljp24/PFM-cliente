<template>
    <div class="layout-historia-animal">
        <v-app>
            <AppBar2 />
            <v-main>
                <v-container>
                    <Nuxt />
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