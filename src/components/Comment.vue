<template>
  <div id="app" class="container" style="width:30%">
    <h1 style="transform: translate(25%, 0%); color:white;font-weight: bolder; font-size:60px">메모장</h1>
    <AddComment />
    <hr>
    <CommentList class="CommentList" style="overflow-x:hidden; overflow-y:auto; height:500px;"/>
  </div>
</template>

<script>
import CommentList from '@/components/CommentList';
import AddComment from '@/components/AddComment';

export default {
  components: {
    CommentList,
    AddComment,
  },
  data() {
    return {
      CommentText: '',
    }
  },
}
</script>
<style>
.CommentList::-webkit-scrollbar {
  width: 10px;
}
.CommentList::-webkit-scrollbar-thumb {
  background-color: whitesmoke;
  border-radius: 10px;
  background-clip: padding-box;
  border: 2px solid transparent;
}
.CommentList::-webkit-scrollbar-track {
  background-color: grey;
  border-radius: 10px;
  box-shadow: inset 0px 0px 5px white;
}
</style>