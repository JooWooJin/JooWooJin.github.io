<template>
  <div>
    <iframe width="0" height="0" :src="url" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    <button @click="play" style="width:60px" class="btn btn-info">재생</button>
    <button @click="stop" style="width:60px" class="btn btn-info">정지</button>
    <button @click="skip" style="width:60px" class="btn btn-info">스킵</button>
  </div>
</template>

<script>
export default {
  data(){
    return{
      url : '',
    }
  },
  methods:{
    play(){
      this.url='';
      var url;
      url = "https://www.youtube.com/embed/";
      var link = this.$store.state.playurl;
      url += link;
      url += "?autoplay=1"
      this.url=url;
      console.log('play');
      this.$store.commit("deletePlayList",0);
    },
    stop(){
      this.url = '';
    },
    skip(){
      this.url ='';
      this.$store.commit("deletePlayList",0);
      this.play();
      console.log('skip');
    }
  },
  components:{
  }
}
</script>

<style>

</style>