<template>
    <div class="module1">
      <transition name="slide-fade">
      <div v-if="state2" class="modal">
        <h3>Submitted!</h3>
      </div>
    </transition>

        <div class="box">
            <ul>
                <li><input  type="text" :placeholder="entries[index]" required/></input></li>
            </ul>
            <div class="buttonG">
              <button type="button" v-on:click="index++ && checkIndex()">Next</button>
              <transition name="fade">
                <button v-if="state" type="button" v-on:click="state2=true">OK</button>
              </transition>
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
            state1:false,
            state2:false
        }
    },
    methods:{
        checkIndex:function(){
            if(this.index>=4){
                this.index=0,
                this.state=true
            }
        }
    },
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Fira+Sans');
    .module1{
        font-family:'Fira Sans', sans-serif;
        max-width: 500px;
        background: #e4e3f7;
        padding: 10px;
        display: flex;
        flex-flow: row;
        flex: 1 1 0;
        border-radius: 0px 0px 5px 5px;
    }
    input[type="text"]{
        font-size: 20px;
        padding: 10px;
        margin: 10px;
    }
    ul{
        list-style-type: none;
        margin: 5px;
        margin-bottom: 10px;
        padding: 15px;
        display: flex;
        flex-flow: column;
        max-height: 60px;
        box-shadow: 0px 0px 45px -15px rgba(0,0,0,0.44);
    }
    .box li{
      background: orange;
      margin-left: 0;
      border-radius: 3px;
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
        box-shadow: 0px 0px 45px -15px rgba(0,0,0,0.44);
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

    .modal{
      text-align: center;
      color: #fff;
      background:#01ba20;
      width: 150px;
      padding: 5px;
      margin-left: 0;
      margin-right: 0;
      border-radius: 30px 30px 3px 30px;
      max-height: 60px;
      box-shadow: 0px 0px 45px -15px rgba(0,0,0,0.44);
    }
  /*Vue js built in transition*/
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}


/* Enter and leave animations can use different */
/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
</style>
