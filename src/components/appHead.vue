<template>
    <div class="appHead" :class="status">
        <input type="text" title="Change title" :value="title">
        <h1>{{status}}</h1>
    </div>
</template>
<script>

import {bus} from '../main';

export default {
     data () {
        return{
            status:""
        }
    },
    props:{
      title:{
        type:String
    },
  },
    methods:{

    },
    //put filters in here and slicing!!!
    filters:{
    },

}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Fira+Sans');

.appHead{
    font-family:'Fira Sans', sans-serif;
    background: purple;
    color: white;
    padding: 10px;
    max-width: 500px;
}
input[type="text"]{
    width: 300px;
    padding: 5px;
    background: purple;
    border: 0;
    font-size: 25px;
    color: white;
}
input[type="text"]:hover{
    cursor: cell;
}
input[type="text"]:active{
    cursor: text;
    border: solid 1px #222;
}
</style>
