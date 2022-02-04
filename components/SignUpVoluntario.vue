<template>
    <div class="sign-up-voluntario">
         <v-form ref="form" v-model="valid" lazy-validation class="mb-6">
                <v-card>
                    <v-card-title class="subtitulo justify-center">Registrarme</v-card-title>
                    <v-card-text>
                        <v-text-field v-model="nombre" placeholder="Nombre (más de 3 caracteres)" required></v-text-field>
                        <v-text-field v-model="email" placeholder="Email" required type="email"></v-text-field>
                        <v-text-field v-model="password" required placeholder="Contraseña (más de 5 caracteres)" type="password"></v-text-field>
                        <v-text-field v-model="password2" required placeholder="Repetir contraseña" type="password"></v-text-field>
                        <p>Acepto las <a @click.stop="dialog = true">condiciones</a></p>
                        <v-dialog v-model="dialog" max-width="400">
                            <v-card>
                                <v-card-title class="text-h5">¿Aceptas las condiciones para ser voluntario?</v-card-title>
                                <v-card-text>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus varius euismod quam, vitae congue urna finibus quis. Praesent cursus justo quis tincidunt malesuada. Nulla sollicitudin orci lectus, at tempus ligula tempor a. Suspendisse posuere tristique ex. Ut eget ligula velit. Aliquam vitae lobortis felis, non fringilla magna. Donec pharetra massa tortor, scelerisque malesuada turpis vulputate quis. Etiam mi leo, blandit sit amet risus vitae, rhoncus fermentum dolor.

Phasellus blandit leo quam, vel congue mauris elementum porttitor. Donec interdum ipsum tellus, id congue risus vehicula ut. Proin eleifend, ligula a auctor sodales, ipsum ex dictum sem, ut ornare lacus nunc sed mi. Etiam nulla dui, iaculis eget sagittis eu, sagittis sit amet justo. Praesent rutrum varius purus at pharetra. Donec malesuada justo vitae lorem rhoncus lacinia. Quisque feugiat metus libero, ultrices feugiat turpis faucibus quis. Sed blandit, justo tempus condimentum fringilla, tortor ante tempus metus, id rutrum neque justo ut odio. Sed sollicitudin quam quis justo dictum, vel egestas dolor tincidunt. Suspendisse diam tellus, malesuada id sagittis nec, posuere in mauris. Ut et semper neque. Mauris convallis felis scelerisque erat porttitor, ac pulvinar eros finibus. Suspendisse vel aliquet mi. Nullam sodales mollis leo eget lacinia. Vestibulum justo est, ullamcorper vitae pretium a, venenatis sit amet erat.

Donec purus dui, faucibus eu semper id, posuere id lorem. Vivamus sagittis augue vel ullamcorper finibus. Phasellus elementum efficitur felis vel rhoncus. Nam urna sem, vulputate at quam sit amet, pellentesque auctor dolor. Quisque tristique lobortis laoreet. Maecenas volutpat dolor et felis eleifend pretium. Maecenas quis vehicula mauris. Morbi ultricies suscipit nunc eu egestas. Suspendisse porttitor dui sed dapibus accumsan. Pellentesque sed auctor dolor. Quisque non sem id nisi fermentum suscipit. Nullam at elementum ante, eget suscipit urna. Nunc vel diam molestie nisi facilisis lacinia eget ut augue. Donec sit amet sem porttitor, rutrum tellus sed, dignissim sapien. Ut eu purus erat. Donec ac sapien lobortis, rhoncus metus vel, convallis nisl.

Duis at gravida neque, ac pulvinar ex. Suspendisse porttitor pharetra mi. Morbi mi augue, sodales a malesuada id, suscipit sit amet orci. Sed efficitur leo non euismod interdum. Praesent eleifend orci a nunc tincidunt, sed posuere leo suscipit. Proin pellentesque ipsum eget finibus porta. Duis vel rhoncus justo.

Etiam ultricies dolor massa, ac aliquet lectus imperdiet at. In id odio ac nunc maximus dictum. Nulla id eros eros. Cras nec odio posuere, posuere turpis et, placerat neque. Curabitur rhoncus aliquet metus, eget viverra orci facilisis faucibus. Duis eget odio arcu. Nunc eu dolor sit amet metus pharetra consequat id in purus. Suspendisse vitae felis dui. Aliquam facilisis ipsum eu orci auctor fermentum. Etiam id cursus felis. Etiam tincidunt nisi lacus, sit amet laoreet sapien mollis vel. In feugiat scelerisque sem non mollis. Pellentesque viverra in ante id interdum. Nam consequat quam eget lacinia consectetur. Duis vestibulum, orci quis bibendum molestie, nisi urna varius erat, non aliquet lorem neque in dolor. In venenatis condimentum nulla, quis porta mi congue non.</v-card-text>
                                <v-card-actions>
                                    <v-spacer></v-spacer>
                                    <v-checkbox v-model="condiciones" label="Acepto las condiciones" required :rules="[v => !!v ||'Debes aceptar condiciones para continuar']" @click="dialog = false"></v-checkbox>
                                </v-card-actions>
                            </v-card>
                        </v-dialog>
                        <v-btn block @click="validate" class="mt-6">Enviar</v-btn>
                    </v-card-text>
                </v-card>    
        </v-form>  
        <a href="/voluntario/sesion">Iniciar Sesión</a>
    </div>
</template>

<script>
export default {
    data(){
        return{
            valid:true,
            nombre:'',
            email:'',
            password:'',
            password2:'',
            condiciones:false,
            dialog: false,
        }
    },
    methods:{
        validate(){
           this.$refs.form.validate();
           if(this.condiciones == true){
                this.onSubmit();
           }
        },
        validateEmail(email) {
            return String(email)
                .toLowerCase()
                .match(
                /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
                );
        },
        async onSubmit(){ 
             if(this.password !== this.password2 ){
                alert("Las contraseñas son diferentes");
                return;
            };
            if(this.password.length <= 5 || this.password2.length <= 5){
                alert("Las contraseñas son demasiado cortas");
                return;
            };
            if(this.nombre.length <= 3){
                alert("nombre demasiado corto");
                return;
            };
            if(this.validateEmail(this.email) === null){
                alert("Email incorrecto");
                return;
            };
            try{
                const body = JSON.stringify({
                    email: this.email,
                    nombre: this.nombre,
                    clave: this.password,
                });
                const res = await fetch('https://reservanimal.herokuapp.com/api/voluntario/crearVoluntario',{
                    method: 'post',
                    headers:{
                        'Content-Type': 'application/json',
                    },
                    body,
                });
                const data = await res.json();
                if(data.error){
                    alert(data.error);
                    return;
                }else{
                    this.$router.push('/voluntario/sesion');
                }
            }catch(err){
                console.log(err);
            }

        },
    }
}
</script>