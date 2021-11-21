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
                    <v-row>
                        <v-col cols="5">
                            <v-img src="https://static.wixstatic.com/media/fdcdcc_5437d96cc15b4cf4bfcf52dabb9685d2~mv2.jpeg/v1/fill/w_280,h_163,fp_0.17_0.4,q_90/fdcdcc_5437d96cc15b4cf4bfcf52dabb9685d2~mv2.jpeg"></v-img>
                        </v-col>
                        <v-col cols="7">
                            <Nuxt />
                        </v-col>
                     </v-row>
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