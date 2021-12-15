<template>
    <div class="historia">
        <v-card>
            <v-row>
                <v-col cols="4">
                    <v-img :src="diario.foto"></v-img>
                </v-col>
                <v-col cols="8">
                    <v-card-text>
                        <h4 class="text-center">{{diario.fecha}}</h4>
                        <p>{{diario.descripcion}}</p>
                    </v-card-text>
                </v-col>
            </v-row>
        </v-card>
    </div>
</template>

<script>
export default {
    props:{
        diario:{
            type:Object,
            required: true,
        }
    },
}
</script>