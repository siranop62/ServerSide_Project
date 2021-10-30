<template>
    <div class="dashboard">
        <Sidebar/>
        <div class="content">
            <router-view/>
        </div>
    </div>
</template>

<script>
import Sidebar from '../components/Sidebar'
export default {
    name: 'Home',

    components: { 
        Sidebar 
    },
}
</script>

<style scoped>
    .dashboard {
        display: grid;
        grid-template-columns: 1fr 5fr;
        background-color: teal;
        height: 125vh;
        width: 100vw;
    }

    .content {
        background-color: white;
    }

    
</style>