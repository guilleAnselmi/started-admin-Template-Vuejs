<template>
<div>

     <v-navigation-drawer
      v-model="drawer"
      app
    >
  <v-list>
          <v-list-group
            v-for="item in items"
            v-model="item.active"
            :key="item.name"
            :prepend-icon="item.icon"
            no-action
          >
            <v-list-tile slot="activator">
              <v-list-tile-content>
                <v-list-tile-title>{{ item.name }}</v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>

            <v-list-tile 
                v-for="subItem in item.subitems"
                :key="subItem.path"
                :to="subItem.path"
   
            >
              <v-list-tile-content>
                <v-list-tile-title>{{ subItem.name }}</v-list-tile-title>
              </v-list-tile-content>

              <v-list-tile-action>
                   <v-icon
                  :to="subItem.path"
                    :class="{active: activeRoute(subItem.path)}"  
                >
                    {{ subItem.icon }}
                </v-icon>

           
              </v-list-tile-action>
            </v-list-tile>
          </v-list-group>
        </v-list>

    </v-navigation-drawer>

    <v-toolbar dark color="primary" fixed app>
        <v-toolbar-side-icon
        @click.stop="drawer = !drawer"
        ></v-toolbar-side-icon>

        <v-toolbar-title class="white--text">{{title}}</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
        <v-icon class="" >search</v-icon>
        </v-btn>
    </v-toolbar>
</div>

</template>

<script>

export default {
    props: {
        title: {type: String, default: 'Nombre Empresa'},
        items: {
            type: Array,
            default: function () {
                return   [
                            {
                                name: 'Group',
                                icon: 'group',
                                subitems: [
                                    {
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
                                    }
                                ]
                            }
                        ]
            }
        }
    },

    data() {
        return{
            drawer: false
        }
    },

    methods: {
        activeRoute: function (item) {
            return this.$route.path === item
        }
    }
}
</script>

<style lang="scss" scoped>
.active {
    color: var(--v-primary-base)
}

</style>
