<template>
        <div class="box">
            <ul>
                <li><input  type="text" placeholder="Entry" v-model="textCon" required/></input></li>
            </ul>
            <div class="buttonG">
              <button type="button" v-on:click="testmyreg">OK</button>
            </div>

            <ul v-for="extract in extracted" class="tableUI">
              <li>{{extract}}</li>
            </ul>
            <h1>{{samplevarjoined}}</h1>
            <ul v-for="arrayF in myArr" class="tableUI">
              <li>{{arrayF}}</li>
            </ul>
        </div>
    </div>
</template>
<script>
export default {
     data () {
        return{
              //colName:userID dataType:integer colName:userName dataType:varchar colName:userPassword dataType:varchar
            //I used already V-MODEL!!
            textCon:"",
            //regexStmtCol:/(colName:(\w+) dataType:(\w+))/g,
            regexStmtCol:/(varchar:\w+ \w+)/gy,
            //regexStmtCol2:/((?<=:)(\w+))/g,
            regexStmtCol2:/(\w+)/g,
            extracted:"",
            samplevarjoined:"",
            myArr:[]
        }
    },
    methods:{
        testmyreg:function(){
            // this.extracted=this.textCon.match(this.regexStmtCol)
            // this.bridge=this.textCon
            // console.log(this.textCon)
            // this.samplevar=this.bridge.match(this.regexStmtCol2)
            // this.samplevarjoined="["+this.samplevar.join(',')+"]"
            // console.log(this.samplevarjoined)
            // I can also get single value and push every value that i get to the specific slot in myArr
            // put a limitation
            this.extracted=this.textCon.match(this.regexStmtCol2)
            console.log(this.extracted)
            this.samplevarjoined="["+this.extracted.join(',')+"]"
            this.myArr.push(this.samplevarjoined)
            console.log(this.samplevarjoined)
            console.log(this.myArr)
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
    button:hover{
        background:#3498db;
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
