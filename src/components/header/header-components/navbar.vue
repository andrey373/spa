<template>
    <div class="header_line_top">
        <div class="container">
            <div class="header_line_inner">
                <button class="toogle_theme" type="button">
                    <svg class="moon" viewBox="0 0 512 512">
                        <path d="M268.279,496c-67.574,0-130.978-26.191-178.534-73.745S16,311.293,16,243.718A252.252,252.252,0,0,1,154.183,18.676a24.44,24.44,0,0,1,34.46,28.958,220.12,220.12,0,0,0,54.8,220.923A218.746,218.746,0,0,0,399.085,333.2h0a220.2,220.2,0,0,0,65.277-9.846,24.439,24.439,0,0,1,28.959,34.461A252.256,252.256,0,0,1,268.279,496ZM153.31,55.781A219.3,219.3,0,0,0,48,243.718C48,365.181,146.816,464,268.279,464a219.3,219.3,0,0,0,187.938-105.31,252.912,252.912,0,0,1-57.13,6.513h0a250.539,250.539,0,0,1-178.268-74.016,252.147,252.147,0,0,1-67.509-235.4Z"/>
                    </svg>
                </button>
                <div class="time_block">{{ date }}</div>
            </div>
        </div>
    </div>
    <div class="container">
        <div class="header_top">
            <a class="logo" href="#">
                <picture>
                    <source type="image/webp" :srcset="`${picture.logo1xWebp} 1x, ${picture.logo2xWebp} 2x`">
                    <img :src="picture.logo1xJpg" alt="Мягкое кресло Манн-Уитни" :srcset="`${picture.logo1xJpg} 1x, ${picture.logo2xJpg} 2x`">
                </picture>
            </a>

            <div class="baner_top">
                <a class="baner_top_link" href="https://accounts.binance.com/ru/register?ref=17025369" target="_blank">
                </a>
            </div>
        </div>
    </div>
    <nav class="menu">
        <div class="container">
            <ul class="menu_list">
                <li class="menu_list_item" v-for="(item, inx) in menuList" :key="inx">
                    <a class="menu_list_link" href="#">{{ item }}</a>
                </li>
            </ul>
        </div>
    </nav>
</template>

<script>
export default {
    data: () => ({

        date: new Intl.DateTimeFormat('ru-RU', {
                dateStyle: 'long',
                timeStyle: 'medium'
            }).format(new Date()),
        interval: null,
        picture: {
            logo1xJpg: require('@/assets/img/icon/logo@1x.jpg'),
            logo2xJpg: require('@/assets/img/icon/logo@2x.jpg'),
            logo1xWebp: require('@/assets/img/icon/logo@1x.webp'),
            logo2xWebp: require('@/assets/img/icon/logo@2x.webp')
        },

        menuList: [
            'Новости',
            'Аналитика',
            'Теханализ',
            'Инструменты',
            'Котировки',
            'Инвестиции',
            'Больше'
        ]
    }),

    methods:{
        dateTime(){
            return new Intl.DateTimeFormat('ru-RU', {
                dateStyle: 'long',
                timeStyle: 'medium'
            }).format(new Date())
        }
        
    },

    mounted(){
        this.interval = setInterval(() => {
            this.date = this.dateTime()
        }, 1000)
    }
}
</script>

<style lang="less">
    .moon{
        fill: #ffffff;
        width: 15px;
        height: 15px;
    }
</style>