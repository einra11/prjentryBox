<template>
  <div id="globe">
      <div class="">
          <app-head class="head1" v-bind:title="title"></app-head>
          <app-entry class="body1"></app-entry>
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
background: #e1e4ea;
}
#globe{
    display: flex;
    justify-content: center;
}
.head1{
  box-shadow: 0px 0px 45px -15px rgba(0,0,0,0.44);
  border-radius: 3px 3px 0px 0px;
}
.body1{
  box-shadow: 0px 0px 45px -15px rgba(0,0,0,0.44);
}
</style>
