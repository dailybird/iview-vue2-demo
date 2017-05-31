<template>
    <Row type="flex" :class="{'sidebar-hide-text' : spanLeft < SIDEBAR_UNFOLD}">
        <i-col class="sidebar" :span="spanLeft">
            <Menu active-name="1" theme="dark" width="auto">
                <div class="sidebar-header">
                    <i-button type="text" @click="toggleFold">
                        <Icon type="navicon" size="16" color="#FFF"></Icon>
                    </i-button>
                </div>
                <Menu-item name="1" class="sidebar-menu-item">
                    <Icon type="ios-navigate" :size="iconSize"></Icon>
                    <span class="sidebar-text">侧边 1</span>
                </Menu-item>
                <Menu-item name="2" class="sidebar-menu-item">
                    <Icon type="ios-keypad" :size="iconSize"></Icon>
                    <span class="sidebar-text">侧边 2</span>
                </Menu-item>
                <Menu-item name="3" class="sidebar-menu-item">
                    <Icon class="sidebar-icon" type="ios-analytics" :size="iconSize"></Icon>
                    <span class="sidebar-text">侧边 3</span>
                </Menu-item>
            </Menu>
        </i-col>

        <i-col class="sidebar-offset" :span="spanLeft"></i-col>

        <i-col :span="spanRight">
            <slot></slot>
        </i-col>
    </Row>
</template>

<script>
    /**
     * 左边栏展开时的大小
     * 注：iview 中栅格系统总长为 24
     * @type {number}
     */
    const SIDEBAR_UNFOLD = 3;

    /**
     * 左边栏收起的大小
     * @type {number}
     */
    const SIDEBAR_FOLD = 1;

    export default {
        data () {
            return {
                SIDEBAR_UNFOLD,
                spanLeft: SIDEBAR_UNFOLD,
                spanRight: 24 - SIDEBAR_UNFOLD,
            }
        },
        computed: {
            iconSize () {
                return this.spanLeft === SIDEBAR_UNFOLD ? 14 : 18;
            }
        },
        methods: {
            toggleFold () {
                if (this.spanLeft === SIDEBAR_UNFOLD) {
                    this.spanLeft = SIDEBAR_FOLD;
                    this.spanRight = 24 - SIDEBAR_FOLD;
                } else {
                    this.spanLeft = SIDEBAR_UNFOLD;
                    this.spanRight = 24 - SIDEBAR_UNFOLD;
                }
            }
        }
    }
</script>

<style scoped>
    /*固定左边栏*/
    .sidebar{
        height: 100%;
        z-index: 10;
        position: fixed;
        background: #464c5b;
        overflow: hidden;
    }

    /*由于 fix 不在正常文档流，是用一个透明 div 实现效果*/
    .sidebar-offset{
        background: transparent;
        overflow: hidden;
    }

    /*控制折叠/展开效果*/
    .sidebar-menu-item{
        padding-left: 20px;
        padding-right: 20px;
        border: 0px;
        background: #464c5b;
    }
    .sidebar-hide-text .sidebar-menu-item{
        padding-left: 0px;
        padding-right: 0px;
        text-align: center;
    }
    .sidebar-hide-text .sidebar-text{
        display: none;
    }

    /*折叠/展开按钮*/
    .sidebar-header{
        height: 30px;
        background: #5b6270;
        box-shadow: 0 1px 1px rgba(0,0,0,.1);
        text-align: center;
    }

    /*图标过渡效果*/
    .ivu-col{
        transition: width .2s ease-in-out;
    }
</style>