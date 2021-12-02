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
                        <p>{{diario.suceso}}</p>
                    </v-card-text>
                </v-col>
            </v-row>
        </v-card>
    </div>
</template>

<script>
export default {
    data(){
        return{
            diario:{
                foto:'https://upload.wikimedia.org/wikipedia/commons/7/76/Atr3e.jpg',
                fecha:'YY/YY/YYYY',
                suceso:'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris eget augue urna. Aenean venenatis aliquet quam in vulputate. Maecenas vitae lectus sed ex luctus congue ut id lectus. Duis massa ex, lacinia eget ultricies et, venenatis nec felis. Nullam metus ex, sollicitudin rutrum hendrerit eu, venenatis a nulla. Nullam rhoncus, est vitae eleifend commodo, felis neque euismod magna, et imperdiet turpis ipsum vitae massa. Nunc quis eleifend turpis.Praesent tempus urna ac tristique tempus. Maecenas bibendum nunc at est accumsan gravida. Maecenas sed posuere sem. Donec tincidunt elementum ligula vitae tincidunt. Donec maximus est in turpis consequat, ut pellentesque mauris viverra. Integer lacus magna, imperdiet eu accumsan non, ultrices ut elit. Integer a eros eleifend, maximus nibh in, accumsan enim. Sed laoreet viverra sollicitudin. Sed luctus massa eu neque fringilla molestie sit amet ut lectus. Nulla tempus lectus in nisl porta congue. Suspendisse sed suscipit dolor. Mauris et massa ac felis sollicitudin ultricies. Phasellus mattis sed nibh sit amet blandit. Phasellus vitae arcu ullamcorper, pharetra tellus non, euismod augue. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Nam feugiat ut nisi eu ullamcorper.Donec lacus mauris, bibendum sit amet neque eu, pharetra faucibus nisl. Nullam ac tellus malesuada, varius purus auctor, maximus eros. Cras ac elit non sapien finibus consectetur at ut augue. Curabitur nec lacus eget mi sollicitudin mattis vel eu lacus. Phasellus consectetur suscipit magna eget elementum. Donec lorem elit, tristique non arcu non, pellentesque congue leo. Donec ac viverra turpis. In vel felis lectus.',
            }
        }
    }
}
</script>