<template>
    <div class="voluntario-idHistoria">
        <Historia :diario="diario"/>
    </div>
</template>

<script>
export default {
    layout:'historiaAnimal',
    data(){
        return{
            diario:'',
        }
    },
    async beforeMount(){
        await this.loadHistory();
    },
    methods:{
        async loadHistory(){
             try{
                const idDiario = this.$route.params.id;
                const res = await fetch(`http://localhost:4500/api/diario/${idDiario}`,
                {
                    headers: {
                    'Content-Type': 'application/json',
                    }
                }
                );
                const data = await res.json();
                if(data.error){
                    alert(data.error);
                }else{
                    this.diario = data.diario;
                };
            }catch(err){
            console.log(err);
        }
        }
    }
}
</script>