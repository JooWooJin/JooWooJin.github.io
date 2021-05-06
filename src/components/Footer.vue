<template>
  <div>
      <button @click="PrevPage" class="btn btn-warning">이전 페이지</button>
      <button @click="NextPage" class="btn btn-warning">다음 페이지</button>
  </div>
</template>

<script>
import axios from 'axios'
import lodash from 'lodash'

export default {
    methods:{
        PrevPage(){
            var vm = this;
            this.url = this.$store.state.url;
            this.token = this.$store.state.prevtoken;
            this.url += "&pageToken=" + this.token;
            axios.get(this.url)
            .then(function(response){
                let obj = [];
                for(var i = 0 ; i < 5 ; i++)
                {
                    obj.push({id : response.data.items[i].id.videoId , title : lodash.unescape(response.data.items[i].snippet.title)});
                }
                console.log(obj);
                vm.$store.commit('addList', obj);
                if(response.data.prevPageToken!=undefined)
                    vm.$store.commit('addPrevToken',response.data.prevPageToken);
                if(response.data.nextPageToken!=undefined)
                    vm.$store.commit('addNextToken',response.data.nextPageToken);
            })
            .catch(function(error){
                console.log(error)
            });
        },
        NextPage(){
            var vm = this;
            this.url = this.$store.state.url;
            this.token = this.$store.state.nexttoken;
            this.url += "&pageToken=" + this.token;
            axios.get(this.url)
            .then(function(response){
                let obj = [];
                for(var i = 0 ; i < 5 ; i++)
                {
                    obj.push({id : response.data.items[i].id.videoId , title : response.data.items[i].snippet.title});
                }
                console.log(obj);
                vm.$store.commit('addList', obj);
                if(response.data.prevPageToken!=undefined)
                    vm.$store.commit('addPrevToken',response.data.prevPageToken);
                if(response.data.nextPageToken!=undefined)
                    vm.$store.commit('addNextToken',response.data.nextPageToken);
            })
            .catch(function(error){
                console.log(error)
            });
        }
    }
}
</script>

<style>

</style>