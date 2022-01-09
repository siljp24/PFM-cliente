<template>
    <div class="layout-perfil" v-if="token">
        <v-app>
            <v-row>
                <v-col cols="12">
                     <AppBar2 />
                </v-col>  
                <v-col>
                    <h2 class="d-flex justify-center">PERFIL</h2>
                </v-col>
            </v-row>
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
    data(){
        return{
            token:''
        }
    },
    beforeMount(){
        this.token = localStorage.getItem('token');
        if(this.token === null || this.token === ''){
            this.$router.push('/')
        }
    }
}
</script>


