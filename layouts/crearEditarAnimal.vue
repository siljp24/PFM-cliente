<template>
    <div class="layout-crear-editar-animal" v-if="token">
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