<template>
    <div class="foto-animal izquierda">
        <img class="foto-animal"
        :src="animal.foto"
        alt="vaca" height="150"
        >
        <h3>{{animal.nombre}}</h3>
    </div>
</template>

<script>
export default {
    data(){
        return{
            animal:{
                foto:'https://storage.contextoganadero.com/s3fs-public/styles/noticias_one/public/ganaderia/field_image/2019-07/datos_curiosos.jpg?itok=K3YrNhVX',
                nombre:'Paca',
            }
            
        }
    }
}
</script>

<style>
.foto-animal{
    border-radius: 50%;
    text-align: center;
}

</style>