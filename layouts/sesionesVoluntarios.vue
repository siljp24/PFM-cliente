<template>
    <div class="layout-sesiones">
        <v-app>
            <v-row>
                <v-col cols="12">
                     <AppBar2 />
                </v-col>  
                <v-col>
                    <h2 class="d-flex justify-center">ÁREA VOLUNTARIOS</h2>
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

<style>
h2{
    color: #558B2F;
}
.subtitulo{
        color:#63828d;
}
</style>