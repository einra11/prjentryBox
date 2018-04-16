<template>
  <div id="globe">
      <div class="">
          <app-head v-bind:title="title"></app-head>
          <app-entry></app-entry>
      </div>
  </div>
</template>

<script>
import appEntry from './components/appEntry.vue';
import appHead from './components/appHead.vue';
export default {
  data () {
    return {
        title:"My title",
    }
},
components:{
    'app-entry':appEntry,
    'app-head':appHead
},
}
</script>

<style>
body{
margin: 0;
margin-top: 40px;
}
#globe{
    display: flex;
    justify-content: center;
}
</style>
