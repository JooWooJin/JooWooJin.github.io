<template>
  <div id="app">
    <h2 style="transform: translate(90%, 0%);color:white;font-size: 90px;width:50%;font-weight: bolder;padding: 0%;margin: 0%;">Play Music</h2>
    <comment style="position:absolute; float: right;transform: translate(240%, 0%); "></comment>
    <br>
    <Search style="transform: translate(90%, 0%); width:50%"></Search>
    <br>
    <List v-bind:sendList="getList" style="transform: translate(50%, 0%); width:60%;"></List>
    <Footer style="transform: translate(110%, 0%); width:45%;"></Footer>
    <controller style="transform: translate(110%, 0%); width:45%;"></controller>
    <play-list style="transform: translate(50%, 0%); width:60%; height:300px"></play-list>
  </div>
</template>

<script>
import Search from './components/Search'
import List from './components/List'
import Footer from './components/Footer.vue'
import PlayList from './components/PlayList.vue'
import Controller from './components/Controller.vue'
import Comment from './components/Comment.vue'

export default {
  name: 'App',
  props: ['sendList'],
  data(){
    return{
    }
  },
  components: {
    Search,
    List,
    Footer,
    PlayList,
    Controller,
    Comment,
  },
}
</script>

<style>
span {
    color:white;
    font-size: 15px;
    font-weight: bolder;
    
}
</style>
