<template>
        <div class="box">
            <div v-show="!submitted">
                <ul>
                    <li><input  type="text" placeholder="Entry" v-model="textCon" required/></input></li>
                </ul>
                <div class="buttonG">
                  <button type="button" v-on:click="testmyreg">OK</button>
                  <button type="button" v-on:click="waiting" v-on:click.prevent="post" :class="state">Submit</button>
                </div>
                <ul v-for="arrayF in myArr" class="tableUI">
                  <li>{{arrayF}}</li>
                </ul>
            </div>
            <transition name="slide-fade">
            <div v-show="submitted" class="success">
                <h1>Submitted</h1>
            </div>
        </transition>
        </div>
    </div>
</template>
<script>
export default {
     data () {
        return{
            textCon:"",
            regexStmtCol:/((varchar|int|text|double|date):\d+ \w+)/gy,
            regexStmtCol2:/(\w+)/g,
            extracted:"",
            extraction2:"",
            samplevarjoined:"",
            samplevar:"",
            myArr:[],
            submitted:false,
            state:""
        }
    },
    methods:{
        testmyreg:function(){
            this.extracted=this.textCon.match(this.regexStmtCol)
            this.samplevar=this.extracted.join('')
            this.extraction2=this.samplevar.match(this.regexStmtCol2)
            this.myArr.push(this.extraction2)
            console.log(this.myArr)
        },
        post:function(){
            this.$http.post('http://jsonplaceholder.typicode.com/posts',{
                array:this.myArr
            }).then(function(data){
                console.log(data);
                this.submitted=true;
                setTimeout(() => this.state="", 200);
            });
        },
        waiting:function(){
          if(this.submitted==false)
          {
            this.state="loading"
          }
          else if (this.submitted==true) {
            this.state=""
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
        margin-top: 0;
        padding: 15px;
        display: flex;
        flex-flow: column;
        max-height: 60px;

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
    .loading{
      background: url(../assets/loading.gif) no-repeat center;
      background-size: 150%;
      text-indent: -10000px;
    }
    .buttonG{
      display: flex;
      flex-flow: row;
      flex: 1 1 0;
      justify-content: center;
    }

    .tableUI{
      list-style: none;
      display:flex;
      flex-flow: column;
      max-width: 200px;
      text-align: center;
      flex:1;
    }
    .success{
        font-family:'Fira Sans', sans-serif;
        padding: 10px;
        background-color: yellow;
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
