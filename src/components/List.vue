<template>
  <div>
      <list-select v-for="select in List" v-bind:key="select.id" :select="select"></list-select>
  </div>
</template>

<script>
import ListSelect from './ListSelect.vue'

export default {
  data(){
    return{
      url : '',
      token : '',
      id : '',
      title : '',
    }
  },
  components:{
    ListSelect
  },
  methods:{
    getList(){
      this.title = this.$store.state.list.title;
      this.id = this.$store.state.list.id;
    },
  },
  computed:{
    List(){
      return this.$store.state.list;
    }
  }
}
</script>

<style>

</style>