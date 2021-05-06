<template>
  <div class="play" style="overflow-x:hidden; overflow-y:scroll;">
      <div v-for="(list, index) in List" :key="list">
      <span style="width:80%;height:100px;">{{ list.title }}</span>
      <button @click="Delete(index)" class="btn btn-danger float-right" >Delete</button>
      <br><br>
      </div>
  </div>
</template>

<script>

export default {
    data(){
        return{
        }
    },
    methods:{
        Delete(index){
            this.$store.commit("deletePlayList",index);
        }
    },
    computed:{
        List(){
            return this.$store.state.playlist;
        }
    }
}
</script>

<style>
div{
    width : 90%;
    border : 2px;
}
span{
    text-overflow: ellipsis;
    height : 20px;
}
.play::-webkit-scrollbar {
  width: 10px;
}
.play::-webkit-scrollbar-thumb {
  background-color: whitesmoke;
  border-radius: 10px;
  background-clip: padding-box;
  border: 2px solid transparent;
}
.play::-webkit-scrollbar-track {
  background-color: grey;
  border-radius: 10px;
  box-shadow: inset 0px 0px 5px white;
}
</style>