<template>
    <div class="layout-animal">
        <v-app>
            <AppBar2 />
            <v-main>
                <v-container>
                    <v-row>
                        <v-col cols="12">
                            <FotoAnimal :animal="animal"/>
                        </v-col>
                    </v-row>
                    <v-row>
                        <Nuxt />
                    </v-row>
                </v-container>
            </v-main>
        </v-app>
    </div>
</template>

<script>
export default {
    data(){
        return{
            animal:{},
            idAnimal:this.$route.params.id,
        }
    },
    async beforeMount(){
        await this.cargarFoto();
    },
    methods:{
        async cargarFoto(){
            try{
                const res = await fetch(`http://localhost:4500/api/animal/${this.idAnimal}`,{
                    method:'get',
                });
                const data = await res.json();
                if(data.error){
                    alert(data.error);
                    return;
                };
                this.animal = data.animal;
            }catch(err){
                console.log(err);
            }
        }
    }
}
</script>