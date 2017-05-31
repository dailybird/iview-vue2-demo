<template>
    <Menu mode="horizontal" theme="dark" active-name="1">
        <div class="layout-logo"></div>
        <div class="layout-nav">
            <Menu-item name="1">
                <Icon type="ios-navigate"></Icon>
                左侧导航1
            </Menu-item>
            <Menu-item name="2">
                <Icon type="ios-keypad"></Icon>
                左侧导航2
            </Menu-item>
            <Menu-item name="3">
                <Icon type="ios-analytics"></Icon>
                左侧导航3
            </Menu-item>
            <Menu-item name="4">
                <Icon type="ios-paper"></Icon>
                左侧导航4
            </Menu-item>
        </div>
        <div class="layout-nav" style="float: right;">
            <Menu-item name="1">
                <Icon type="ios-navigate"></Icon>
                右侧导航1
            </Menu-item>
            <Menu-item name="2">
                <Icon type="ios-keypad"></Icon>
                右侧导航2
            </Menu-item>

            <Submenu name="3" trigger="click">
                <template slot="title">
                    <Icon type="stats-bars"></Icon>
                    USERNAME
                </template>
                <Menu-item name="3-1">新增和启动</Menu-item>
                <Menu-group title="使用">
                    <Menu-item name="3-1">新增和启动</Menu-item>
                    <Menu-item name="3-2">活跃分析</Menu-item>
                    <Menu-item name="3-3">时段分析</Menu-item>
                </Menu-group>
                <Menu-group title="留存">
                    <Menu-item name="3-4">用户留存</Menu-item>
                    <Menu-item name="3-5">流失用户</Menu-item>
                </Menu-group>
            </Submenu>

        </div>
    </Menu>
</template>

<script>
    export default {
        data () {
            return {

            }
        }
    }
</script>

<style scoped>

</style>