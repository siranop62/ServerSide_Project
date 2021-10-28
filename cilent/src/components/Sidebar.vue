<template>
    <div class="sidebar">
        <div class="title">
            Simple Sidebar
        </div>
        <div class="manu-item">
            <router-link to="/" active-class="active" exact tag="button" class="side-btn">
                <div class="link-container">
                    Overview
                </div>
            </router-link>
            <router-link to="/product" active-class="active" exact tag="button" class="side-btn">
                <div class="link-container">
                    Product
                </div>
            </router-link>
            <router-link to="/login" active-class="active" exact tag="button" class="side-btn">
                <div class="link-container">
                    Login
                </div>
            </router-link>
            <router-link to="/" active-class="active" exact tag="button" class="side-btn">
                <div class="link-container"> 
                    <a v-on:click.prevent="logout" href="#">
                    Logout 
                    </a>
                </div>
            </router-link>
        </div>
    </div>
</template>

<script>
export default {
    methods:{
  logout () {
          this.$store.dispatch('setToken', null)
          this.$store.dispatch('setUser', null)
          this.$router.push({
            name: 'login'
    })
    }
  }
}
</script>

<style scoped>
    .title {
        color: rgb(255, 255, 255);
        font-size: 30px;
        margin-top: 60px;
    }

    .manu-item {
        display: flex;
        flex-direction: column;
        margin-top: 20px;
    }

    .manu-item > * {
        margin-top: 60px;
    }

    .side-btn:focus {
        outline: none;
    }

    .side-btn.active {
        background-color: rgb(154, 210, 255);
        color: rgb(0, 110, 138);
        font-weight: 500;
    }

    .side-btn {
        border: none;
        padding: 16px 0px;
        cursor: pointer;
        font-size: 16px;
        color: rgb(156, 135, 253);
    }

    .clearfix {
        clear: left;
    }
</style>