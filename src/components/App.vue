<template>
    <div>
        <Navbar></Navbar>
        <Sidebar>
            <router-view>

            </router-view>
        </Sidebar>
    </div>
</template>

<script>
    import Navbar from './layouts/Navbar';
    import Sidebar from './layouts/Sidebar';
    export default {
        components: {
            Navbar, Sidebar
        }
    }
</script>

<style scoped>

</style>