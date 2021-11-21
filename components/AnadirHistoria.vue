<template>
    <div class="añadir-historia">
        <v-form>
            <v-card>
                <v-card-title class="justify-center"> HISTORIA</v-card-title>
                <v-card-text>
                    <v-file-input v-model="foto" placeholder="Foto"></v-file-input>
                    <v-menu ref="menu" v-model="menu" :close-on-content-click="false" :return-value.sync="date" transition="scale-transition" offset-y min-width="auto"
                    >
                        <template v-slot:activator="{ on, attrs }">
                            <v-text-field v-model="date" label="Fecha" prepend-icon="mdi-calendar" readonly v-bind="attrs" v-on="on"
                            ></v-text-field>
                        </template>
                        <v-date-picker v-model="date" no-title scrollable>
                            <v-spacer></v-spacer>
                            <v-btn text color="primary" @click="menu = false">Cancel</v-btn>
                            <v-btn text color="primary" @click="$refs.menu.save(date)">OK</v-btn>
                        </v-date-picker>
                    </v-menu>
                    <v-textarea v-model="suceso" placeholder="Suceso" required></v-textarea>
                </v-card-text>
                <v-btn block  disabled elevation="2"> ENVIAR</v-btn>
            </v-card>
        </v-form> 
    </div>
</template>

<script>
export default {
    data(){
        return{
            date:(new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
            foto: undefined,
            suceso:'',
            menu: false,
        }
    }
}
</script>