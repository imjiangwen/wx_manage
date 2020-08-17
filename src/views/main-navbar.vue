<template>
    <nav class="site-navbar" style="background-color:white;" :class="'site-navbar--' + navbarLayoutType">
        <div class="site-navbar__header">
            <h1 class="site-navbar__brand" @click="$router.push({ name: 'home' })">
                <a class="site-navbar__brand-lg" style="color:#000000;" href="javascript:;">迷你微信后台</a>
                <a class="site-navbar__brand-mini" href="javascript:;" style="color:#000000;">W</a>
            </h1>
        </div>
        <div class="site-navbar__body clearfix">
            <el-menu class="site-navbar__menu" mode="horizontal">
                <el-menu-item class="site-navbar__switch" index="0" @click="sidebarFold = !sidebarFold">
                    <i :class="sidebarFold?'el-icon-s-unfold':'el-icon-s-fold'"></i>
                </el-menu-item>
            </el-menu>
            <el-menu class="site-navbar__menu" mode="horizontal">
                <el-menu-item index="2">
                    <template slot="title">
                        <wx-account-selector></wx-account-selector>
                    </template>
                </el-menu-item>
            </el-menu>
        </div>
    </nav>
</template>

<script>
import WxAccountSelector from '@/components/wx-account-selector'
export default {
    components: {
        WxAccountSelector
    },
    computed: {
        navbarLayoutType: {
            get() { return this.$store.state.common.navbarLayoutType }
        },
        sidebarFold: {
            get() { return this.$store.state.common.sidebarFold },
            set(val) { this.$store.commit('common/updateSidebarFold', val) }
        },
        mainTabs: {
            get() { return this.$store.state.common.mainTabs },
            set(val) { this.$store.commit('common/updateMainTabs', val) }
        },
        userName: {
            get() { return this.$store.state.user.name }
        }
    },
    methods: {
      // 查看机构的公众号 todo


    }
}
</script>
