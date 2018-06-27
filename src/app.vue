<template>
    <div id="main" class="app-main">
        <router-view></router-view>  
    </div>
</template>

<script>
import Cookies from 'js-cookie';
import axios from 'axios'

    export default {
        data () {
            return {
                theme: this.$store.state.app.themeColor
            };
        },
        mounted(){
          // console.log(Cookies.set('user'))
        },
        methods: {
          
        }
    };
</script>

<style>
/*scoped*/
html,body{
    width: 100%;
    height: 100%;
    background: #f0f0f0;
    overflow: hidden;
}
.app-main{
    width: 100%;
    height: 100%;
}
.cf:after {
    clear: both;
    visibility: hidden;
    font-size: 0;
    height: 0;
}
.cf:after, .cf:before {
    content: "";
    display: table;
}
 pre {
     display: none;
     background: #495060;
     color: #e2e2e2;
     padding: 10px;
     border-radius: 10px;
     max-height: 300px;
     overflow: auto;
 }
 input,textarea,select{
  -webkit-appearance: none !important;
 }
 .input-group input{
   border-radius:0 !important;
 }
 .input-group span{
   border-radius:0 !important;
 }
 .hide{
   height:50vh;
   overflow:hidden;
 }
</style>
