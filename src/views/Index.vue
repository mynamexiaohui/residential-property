<template>
    <div class="layout">
        <Layout>
            <ContentHeader></ContentHeader>
            <Layout style="height:calc(100vh - 60px);">
                <Sider collapsible :collapsed-width="100" v-model="isCollapsed" class="menu">
                    <leftMenu @changeCollapsed="changeCollapsed" :isCollapsed="isCollapsed"></leftMenu>
                </Sider>
                <Layout :style="{padding: '0 24px 24px'}">
                    <ContentBreadCrumb></ContentBreadCrumb>
                    <Content
                        :style="{padding: '24px', minHeight: '280px', background: '#fff'}"
                    >Content</Content>
                </Layout>
            </Layout>
        </Layout>
    </div>
</template>

<script>
import ContentHeader from "../components/ContentHeader";
import leftMenu from "../components/LeftMenu";
import ContentBreadCrumb from "../components/ContentBreadCrumb";
export default {
    data() {
        return {
            openNames: ["1"],
            isCollapsed: false
        };
    },
    watch: {},

    methods: {
        changeCollapsed(val) {
            window.console.log(val);
            this.isCollapsed = val;
        }
    },
    computed: {},
    components: {
        ContentHeader,
        leftMenu,
        ContentBreadCrumb
    }
};
</script>

<style>
.layout {
    background: #f5f7f9;
    position: relative;
    overflow-x: hidden;
    overflow-y: scroll;
}
.layout-logo {
    height: 30px;
    color: #fff;
    border-radius: 3px;
    float: left;
    position: relative;
    top: 15px;
    left: 20px;
    line-height: 30px;
    font-size: 20px;
}
</style>