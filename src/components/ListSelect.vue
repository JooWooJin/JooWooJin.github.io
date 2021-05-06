<template>
  <div class="mb-2 d-flex">
        <div>
        <span
            class="ml-3 flex-grow-1"
        >
        {{ select.title}}
        </span>
        </div>
        <button
            v-if="select.id != ''"
            class="btn btn-info"
            @click="Add"
        >Add</button>
    </div>
</template>

<script>
export default {
    props: {
        select : {
            type: Object,
        }
    },
    methods:{
        Add(){
            console.log(this.select.id);
            this.$store.commit('addPlayList',{id : this.select.id, title: this.select.title });
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
span::-webkit-scrollbar {
width: 10px;
}
span::-webkit-scrollbar-thumb {
background-color: #2f3542;
border-radius: 10px;
background-clip: padding-box;
border: 2px solid transparent;
}
span::-webkit-scrollbar-track {
background-color: grey;
border-radius: 10px;
box-shadow: inset 0px 0px 5px white;
}
</style>