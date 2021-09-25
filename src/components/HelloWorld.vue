<template>
  <div class="hello">
   <h3>我是axios,用来发送请求，拦截响应</h3>
   <button @click='getdata'>点击发起get请求</button>
    <button @click='postdata'>点击发起post请求</button>
   <ul>
     <li v-for="item in items">{{item.title}}</li>
   </ul>
  </div>
</template>

<script>
import axios from 'axios'
import Vue from 'vue'
import qs from 'qs'

Vue.prototype.$http=axios

export default {
  name: 'HelloWorld',
  data () {
    return {
     items:[],
    }
  },
  methods:{
    getdata:function(){
      var self =this
      this.$http.get('https://cnodejs.org/api/v1/topics',{
            params:{
               page:1,
                limit:15
             }
      })
      .then(function(res){
            console.log(res)
            self.items=res.data.data
            
      })
      .catch(function(err){
            console.log(err)
      })
    },
    postdata:function(){
      var self =this
      this.$http.post(url,qs.stringify({
        page:1,
        limit:20
      }))
      .then(function(res){
            console.log(res)
            self.items=res.data.data
            
      })
      .catch(function(err){
            console.log(err)
      })
    },
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
