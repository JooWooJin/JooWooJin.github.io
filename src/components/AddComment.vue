<template>
    <input
        v-model="CommentText"
        type="text"
        placeholder="Write Comment Here"
        @keyup.enter="addComment"
        style="
        font-size: 40px;
        font-weight: bolder;
        color:white;
        height:50px;
        width:80%;
        border:none;border-right:0px;
        border-top:0px;
        boder-left:0px;
        boder-bottom:0px;
        background: transparent;"
    >
</template>

<script>
export default {
    data() {
        return {
            CommentText: '',
        }
    },
    methods: {
        addComment(e) {
            if(e.target.value != '' && e.target.value != undefined)
            {
                this.$store.commit('ADD_COMMENT', e.target.value);
                this.CommentText = '';
            }
        }
    }
}
</script>

<style>

</style>
