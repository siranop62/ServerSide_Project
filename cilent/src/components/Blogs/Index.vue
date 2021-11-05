<template>
    <div class="blogs">
        <h2> Get all work </h2>

        <!-- <p><button v-on:click="logout"> Logout </button></p> -->

        <hr/><h4> Number of tasks {{blogs.length}}</h4>
        <b-button-group><p>
            <b-button variant="success" v-on:click="navigateTo('/blog/create')"> Create work </b-button>
        </p></b-button-group>
        <div v-for="blog in blogs" v-bind:key="blog.id">
            <p>id: {{ blog.id }} </p>
            <p>Title: {{ blog.title }} </p>
            <p>Address and Task detail : {{ blog.content }} </p>
            <p>Category : {{ blog.category }} </p>
            <p>Status: {{ blog.status }} </p>
            <b-button-group><p>
                <b-button v-on:click="navigateTo('/blog/'+ blog.id)"> View work details</b-button>
                <b-button v-on:click="navigateTo('/blog/edit/'+ blog.id)"> Edite work </b-button>
                <b-button v-on:click="deleteBlog(blog)"> Delete </b-button>
            </p></b-button-group>
            <hr>
        </div>
    </div>
</template>
<script>
import BlogsService from '@/services/BlogsService'
export default {
    data () {
        return { 
            blogs: []
        }
    },
    async created () {
        this.blogs = (await BlogsService.index()).data
    },
    methods: {
       /*  logout () {
            this.$store.dispatch('setToken', null)
            this.$store.dispatch('setBlog', null)
            this.$router.push({
                name: 'login'
            })
        }, */
        navigateTo (route) {
            this.$router.push(route)
        },
        async deleteBlog (blog) {
            let result = confirm("Want to delete?")
            if (result) {
                try {
                    await BlogsService.delete(blog)
                    this.refreshData()
                } catch (err) {
                    console.log(err)
                }
            }
        },
        async refreshData() {
            this.blogs = (await BlogsService.index()).data
        }
    }
}
</script>
<style scoped>
    .blogs {
        margin-left: 10px;
        margin-top: 10px;
        margin-right: 10px;
    }
</style>
