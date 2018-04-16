<template>
    <div class="module1">
        <div class="box">
            <ul>
                <li><input  type="text" :placeholder="entries[index]" required/></input></li>
            </ul>
            <div class="buttonG">
              <button type="button" v-on:click="index++ && checkIndex()">Next</button>
              <button v-if="state" type="button">OK</button>
            </div>
        </div>

    </div>
</template>

<script>
export default {
     data () {
        return{
            textSize:null,
            textDesc:"",
            entries:['Name','Size', 'Description','DataType'],
            index:0,
            state:false
        }
    },
    methods:{
        checkIndex:function(){
            if(this.index>=4){
                this.index=0,
                this.state=true
            }
        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Fira+Sans');
    .module1{
        font-family:'Fira Sans', sans-serif;
        max-width: 500px;
        background: #f0eeeb;
        padding: 10px;
    }
    input[type="text"]{
        font-size: 20px;
        padding: 10px;
        margin: 10px;
    }
    ul{
        list-style-type: none;
        margin: 0;
        padding: 15px;
        display: flex;
        flex-flow: column;
    }
    button{
        border-radius: 46px 45px 45px 45px;
        background:#3498ca;
        border-radius: 28px;
        font-family: Arial;
        color: #ffffff;
        font-size: 30px;
        padding: 10px 20px 10px 20px;
        border: 0;
        margin: 0px 10px 10px 10px;
    }
    button:hover{
        background:#3498db;
    }
    .buttonG{
      display: flex;
      flex-flow: row;
      flex: 1 1 0;
      justify-content: center;
    }
</style>
