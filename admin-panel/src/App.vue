<template>
  <v-app dark>

    <BaseHeader/>



    <v-content>
      <router-view/>
    </v-content>

    
    <BaseFooter/>
  </v-app>
</template>

<script>
import HelloWorld from '@/components/HelloWorld'
import BaseHeader from '@/components/layout/BaseHeader';
import BaseFooter from '@/components/layout/BaseFooter';

export default {
  name: 'App',
  components: {
    HelloWorld,
    BaseHeader,
    BaseFooter
    
  },
  data () {
    return {
    }
  }
}
</script>

