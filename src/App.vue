<template>
  <v-app>
    <Mainnavbar/>
    <Imglist/>
    <v-main>
    </v-main>
  </v-app>
</template>

<script>
import Imglist from './components/imagel';
import Mainnavbar from './components/nav';
export default {
  name: 'App',

  components: {
    Imglist,
    Mainnavbar
    

  },

  data: () => ({
    //
  }),
};
</script>
<style>
* {
  box-sizing: border-box;
}
</style>
