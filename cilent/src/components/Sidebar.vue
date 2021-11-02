<template>
    <div class="sidebar">
        <div class="title"><center>  
            <div class="img">
                <p><img src="../assets/logo.jpg"></p>
            </div>
            House Flipper
        </center></div>
        <div class="manu-item">
            <router-link :to="{ name: 'home' }" active-class="active" exact tag="button" class="side-btn">
                <div class="link-container">
                    Home
                </div>
            </router-link>
            <router-link :to="{ name: 'blogs' }" active-class="active" exact tag="button" class="side-btn">
                <div class="link-container">
                    Works
                </div>
            </router-link>
            <router-link :to="{ name: 'users' }" active-class="active" exact tag="button" class="side-btn">
                <div class="link-container">
                    Users Account
                </div>
            </router-link>
            <router-link :to="{ name: 'login' }" active-class="active" exact tag="button" class="side-btn">
                <div class="link-container">
                    Login
                </div>
            </router-link>
            <router-link active-class="active" exact tag="button" class="side-btn">
                <div class="link-container">
                    <a v-on:click="logout" a href="login"> Logout</a>
                </div>
            </router-link>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
    logout() {
            this.$store.dispatch("setToken", null);
            this.$store.dispatch("setBlog", null);
            this.$router.push({
                name: "login",
            });
        },
    }
};
</script>

<style scoped>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300&family=Ubuntu:wght@300&display=swap');
    .title {
        font-family: 'Ubuntu', sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: rgb(255, 255, 255);
        font-size: 40px;
        margin-top: 60px;
    }

    .manu-item {
        display: flex;
        flex-direction: column;
        margin-top: 10px;
        margin-left: 6px;
    }

    .manu-item > * {
        margin-top: 60px;
    }

    .side-btn:focus {
        outline: none;
    }

    .side-btn.active {
        position: relative;
        background-color: white;
        color: rgb(0, 110, 138);
        font-weight: 500;
        margin-left: 6px;
        border-radius: 5px 0 0 5px;
    }

    .side-btn.active::before{
        position: absolute;
        content: "";
        top: -30px;
        right: 0;
        height: 30px;
        width: 30px;
        background-color: white;
    }

    .side-btn.active::after{
        position: absolute;
        content: "";
        bottom: -30px;
        right: 0;
        height: 30px;
        width: 30px;
        background-color: white;
    }

    .side-btn {
        border: none;
        padding: 16px 0px;
        cursor: pointer;
        font-size: 16px;
        color: white;
        background-color: transparent;
    }

    .side-btn.active .link-container::before {
        position: absolute;
        top: -60px;
        right: 0;
        content: "";
        height: 60px;
        width: 60px;
        border-radius: 50%;
        background-color: teal;
    }

    .side-btn.active .link-container::after {
        position: absolute;
        bottom: -60px;
        right: 0;
        content: "";
        height: 60px;
        width: 60px;
        border-radius: 50%;
        background-color: teal;
        z-index: 99;
    }

    div.img img {
        width: 250px;
        height: 250px;
    }


</style>