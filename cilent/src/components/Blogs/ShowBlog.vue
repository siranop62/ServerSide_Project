<template>
    <div class="sb">
        <h1> Show work </h1>
            <p>id: {{ blog.id }} </p>
            <p>Title : {{ blog.title }} </p>
            <p>Address and Task detail : {{ blog.content }} </p>
            <p>Category : {{ blog.category }} </p>
            <p>Status : {{ blog.status }} </p>
            <b-button-group><p>
                <b-button v-on:click="navigateTo('/blog/edit/'+blog.id)"> Edite task </b-button>
                <b-button v-on:click="navigateTo('/blogs')"> Back </b-button>
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
        margin-top: 10px;
        margin-right: 10px;
    }
</style>
