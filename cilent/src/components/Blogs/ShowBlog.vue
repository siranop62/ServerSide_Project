<template>
    <div class="sb">
        <h1> Show Blog </h1>
            <p>id: {{ blog.id }} </p>
            <p>title: {{ blog.title }} </p>
            <p>content: {{ blog.content }} </p>
            <p>category: {{ blog.category }} </p>
            <p>status: {{ blog.status }} </p>
            <b-button-group><p>
                <b-button v-on:click="navigateTo('/blog/edit/'+blog.id)"> แก้ไขblog </b-button>
                <b-button v-on:click="navigateTo('/blogs')"> กลับ </b-button>
            </p></b-button-group>
    </div>
</template>
<script>
import BlogsService from '@/services/BlogsService'
export default {
    data () {
        return { 
            blog: null
        }
    },
    async created () {
        try {
            let blogId = this.$route.params.blogId
            this.blog = (await BlogsService.show(blogId)).data
        } catch (error) {
            console.log (error)
        }
    },
    methods: {
       navigateTo (route) {
           this.$router.push(route)
       },
    }
}
</script>
<style scoped>
.sb {
        margin-left: 10px;
        margin-top: 10;
        margin-right: 10;
    }
</style>