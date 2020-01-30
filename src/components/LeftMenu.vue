<template>
    <Menu
        ref="leftMenu"
        class="menu-container"
        active-name="1-2"
        theme="dark"
        width="auto"
        :class="menuitemClasses"
        @on-open-change="changeCollapsed"
        @on-select="changeCollapsed"
        :open-names="openNames"
    >
        <Submenu name="1">
            <template slot="title">
                <Icon type="ios-body"></Icon>
                <span>员工管理</span>
            </template>
            <MenuItem name="1-1">Option 1</MenuItem>
            <MenuItem name="1-2">Option 2</MenuItem>
            <MenuItem name="1-3">Option 3</MenuItem>
        </Submenu>
        <Submenu name="2">
            <template slot="title">
                <Icon type="ios-settings"></Icon>
                <span>房屋信息管理</span>
            </template>
            <MenuItem name="2-1">Option 1</MenuItem>
            <MenuItem name="2-2">Option 2</MenuItem>
            <MenuItem name="2-3">Option 3</MenuItem>
        </Submenu>
        <Submenu name="3">
            <template slot="title">
                <Icon type="ios-search"></Icon>
                <span>业主管理</span>
            </template>
            <MenuItem name="3-1">Option 1</MenuItem>
            <MenuItem name="3-2">Option 2</MenuItem>
            <MenuItem name="3-3">Option 3</MenuItem>
        </Submenu>
        <Submenu name="4">
            <template slot="title">
                <Icon type="ios-search"></Icon>
                <span>业主管理</span>
            </template>
            <MenuItem name="4-1">Option 1</MenuItem>
            <MenuItem name="4-2">Option 2</MenuItem>
            <MenuItem name="4-3">Option 3</MenuItem>
        </Submenu>
        <Submenu name="5">
            <template slot="title">
                <Icon type="ios-search"></Icon>
                <span>业主管理</span>
            </template>
            <MenuItem name="5-1">Option 1</MenuItem>
            <MenuItem name="5-2">Option 2</MenuItem>
            <MenuItem name="5-3">Option 3</MenuItem>
        </Submenu>
    </Menu>
</template>

<script>
export default {
    props: {
        isCollapsed: Boolean
    },
    data() {
        return {
            openNames: ["1"]
        };
    },
    watch: {
        isCollapsed(val) {
            if (val) {
                this.openNames = [""];
                this.$nextTick(() => {
                    this.$refs.leftMenu.updateOpened();
                });
            } else {
                this.changeCollapsed();
            }
        }
    },
    methods: {
        changeCollapsed() {
            this.$emit("changeCollapsed", false);
        }
    },
    computed: {
        menuitemClasses: function() {
            return ["menu-item", this.isCollapsed ? "collapsed-menu" : ""];
        }
    }
};
</script>

<style>
/* .layout-con {
    height: 100%;
    width: 100%;
} */
.menu-item .ivu-menu-submenu-title {
    text-align: left;
}
.menu-item .ivu-menu-item {
    padding-left: 25px !important;
}
.menu-item span {
    display: inline-block;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    vertical-align: bottom;
    transition: width 0.2s ease 0.2s;
}
.menu-item i {
    transform: translateX(0px);
    transition: font-size 0.2s ease, transform 0.2s ease;
    vertical-align: middle;
    font-size: 16px;
}
.collapsed-menu .ivu-icon-ios-arrow-down {
    display: none;
}
.collapsed-menu .ivu-menu-submenu-title {
    text-align: center;
}
.collapsed-menu span {
    width: 0px;
    transition: width 0.2s ease;
}
.collapsed-menu i {
    transform: translateX(5px);
    transition: font-size 0.2s ease 0.2s, transform 0.2s ease 0.2s;
    vertical-align: middle;
    font-size: 22px;
}

.menu-container {
    overflow-y: scroll;
    height: calc(100% - 48px);
}
.menu-container::-webkit-scrollbar {
    width: 0 !important;
}
.menu .ivu-layout-sider-trigger {
    background: none;
}

</style>