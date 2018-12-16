<template>
    <v-footer height="auto" class="grey darken-3" >
        <v-layout  wrap justify-center>
            <v-btn :to="item.path" v-for="item in items">{{item.name}}</v-btn>
            
            <v-flex xs12 py-3 text-xs-center white--text>
                &copy;{{copyright.year}} —
                <strong>{{copyright.name}}</strong>
            </v-flex>
        </v-layout>
    </v-footer>
</template>

<script>
export default {

props: {  
    items: {
        type: Array,
        default: function () {
            return  [{
                    name: 'home',
                    path: '/',
                    icon: 'home'
                }, 
                {
                    name: 'about',
                    path: '/about',
                    icon: 'share'

                },
                {
                    name: 'HelloWorld',
                    path: '/hello',
                    icon: 'pan_tool'
            }]
        }
    },
    copyright:  {
        type: Object,
        default: function () {
            return { year: 2018, name: 'Guillermo O. Anselmi'}
        }
    }
},

data () {
    return {

        }
    }

}
</script>

<style lang="scss" scoped>

</style>
