<template>
    <component :is="layout">
      <router-view/>
    </component>
</template>

<script>
import HomeLayout from './views/HomeLayout.vue'
export default {
    computed: {
        layout(){
            return (this.$route.meta.layout || 'main') + '-layout';
        }
    },
    components:{
        'home-layout': HomeLayout
    }
}
</script>

<style lang="less">
    @import './assets/style/style.less';
    @import './assets/style/fonts.css';
</style>
