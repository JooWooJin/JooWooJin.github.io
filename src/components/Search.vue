<template>
  <div style="transform: translate(42%, 0%);">
      <input type="text" v-model="tag" @keyup.enter="getList" placeholder="Input Search Text" style="
    font-size: 40px;
    font-weight: bolder;
    color:white;
    height:50px;
    width:50%;
    border:none;border-right:0px;
    border-top:0px;
    boder-left:0px;
    boder-bottom:0px;
    background: transparent;">
      <button @click="getList" class="btn btn-success">노래검색</button>
  </div>
</template>

<script>
import axios from 'axios'
import lodash from 'lodash'
export default {
    data(){
        return{
            tag : '',
            t : '',
        }
    },
    methods:{
        getList(){
            var vm = this;
            var url = "https://www.googleapis.com/youtube/v3/search?part=snippet&order=relevance&q=";                 
            url += encodeURIComponent(this.tag);
            url += "&key=AIzaSyDPF6QQv0tRMU3Hgf-qZHZ0HcOnIDRr4SY";
            this.tag = '';
            console.log(url);
            this.$store.commit('setUrl',url);
            axios.get(url)
            .then(function(response){
                console.log(response); 
                let obj = [];
                for(var i = 0 ; i < 5 ; i++)
                {
                    obj.push({id : response.data.items[i].id.videoId , title : lodash.unescape(response.data.items[i].snippet.title)});
                }
                console.log(obj);
                vm.$store.commit('addList', obj);
                if(response.data.nextPageToken!=undefined)
                    vm.$store.commit('addNextToken',response.data.nextPageToken);
            })
            .catch(function(error){
                console.log(error)
            });
        },
    }
}
</script>

<style>
input::placeholder{
    color:white;
}
</style>