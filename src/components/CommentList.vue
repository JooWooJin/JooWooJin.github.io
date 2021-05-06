<template>
    <div style="height : 80%">
        <div class="mb-2 d-flex" v-for="(Comment,index) in Comments"
            :key="Comment"
            :Comment="Comment"
            >
            <span
                class="ml-3 flex-grow-1"
            >
                {{ Comment }}
            </span>
            <button
                class="btn btn-danger btn-sm"
                @click="clickDelete(Comment,index)"
            >Delete</button>
        </div>
    </div>
</template>

<script>
export default {
    components: {
    },
    computed: {
        Comments() {
            return this.$store.state.Comments;
        }
    },
    methods: {
        clickDelete(Comment,index) {
            var obj = {comment : Comment, index : index}
            console.log(obj);
            this.$store.commit('DELETE_COMMENT', obj);
        }
    }
}
</script>

<style>

</style>
