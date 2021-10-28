<template>
    <div class="login">
        <h1> User Login </h1> <hr/>
        <form v-on:submit.prevent="onLogin">
            <p>Username: <input type="text" v-model="email" /></p>
            <p>Password: <input type="password" v-model="password" /></p>
            <p><button type="submit">Login </button></p>
            <dev class = "error" v-if="error">{{error}}</dev>
        </form>
    </div>
</template>

<script>
import AuthenService from '@/services/AuthenService'

export default {
    data () {
        return {
            email: '',
            password: ''
        };
    },
    methods:{
        async onLogin () {
            try {
                const response = await AuthenService.login({
                    email: this.email,
                    password: this.password,
                    error: null
                });

                this.$store.dispatch('setToken',response.data.token)
                this.$store.dispatch('setUser',response.data.user)

                this.$router.push({
                   name: 'users'
                 })
                console.log(response)

            } catch (error) {
                console.log(error)
                this.error = error.response.data.error
                this.email = ''
                this.password = ''
            }
        },
    },
}
</script>

<style scoped>
    .error{
    color: red;
  }

    button{
	    height:40px;
	    padding: 5px 5px;
	    margin: 10px 0px;
	    font-weight:bold;
	    background-color:#be5256;
	    border:none;
	    color:#e0dada;
	    cursor:pointer;
	    font-size:16px;
    }

    button:hover{
	    background-color:#711f1b;
    }


</style>