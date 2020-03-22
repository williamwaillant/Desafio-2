<template>
<div class="container-fluid">
    <Header class="fixed" :companyName="company" @displayMobileMenu="displayMobileMenu = !displayMobileMenu"/>
    <MenuMobile v-if="displayMobileMenu" class="fixed margin-menu-mobile"/>
    <div class="row" style="min-height: 200px;">
        <Menu v-if="width >= 768" class="col-md-3 col-lg-2 h-100" style="margin-top: 45px;"/>
        <Content class="col-12 col-md-9 offset-md-3 col-lg-10 offset-lg-2" style="margin-top: 60px"/>
    </div>
</div>
</template>

<script>
import Header from './components/vHeader'
import Menu from './components/vMenu'
import MenuMobile from './components/vMenuMobile'
import Content from './components/vContent'

export default {
    name: 'App',
    components: {
        Header,
        Menu,
        MenuMobile,
        Content
    },
    data() {
        return {
            company: 'Company Name',
            displayMobileMenu: false,
            width: null,
            marginTop: 52,
        };
    },
    methods: {
        onResize(event) {
            this.width = event.target.innerWidth;
            this.displayMobileMenu = false;
        }
    },
    mounted() {
        window.addEventListener('resize', this.onResize)
        this.width = window.innerWidth;
    },
    beforeDestroy() {
        window.removeEventListener('resize', this.onResize)
    }
}
</script>

<style scoped>
.fixed {
    position: fixed;
    z-index: 1;
}

.margin-menu-mobile {
    margin-top: 52px;
    left: 0;
}
</style>