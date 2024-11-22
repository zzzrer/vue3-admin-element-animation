<template>
    <div class="content" ref="home_content">
        <HomeNav ref="home_nav"></HomeNav>
        <HomeBanner :show-list="imagesList" ref="home_banner"></HomeBanner>
        <AnimationFold ref="animation_fold"></AnimationFold>
        <AnimationCard ref="animation_card"></AnimationCard>
        <AnimationClose ref="animation_close"></AnimationClose>
        <FooterTemp></FooterTemp>
    </div>
</template>

<script setup name="home">
//不需要暴露对象
import { ref, onMounted } from "vue";
import HomeNav from "./HomeNav.vue";
import HomeBanner from "./HomeBanner.vue";
import AnimationCard from "./AnimationCard.vue";
import AnimationClose from "./AnimationClose.vue";
import AnimationFold from "./AnimationFold.vue";
import FooterTemp from './FooterTemp.vue';
const a = ref(0);
const home_content = ref(null);
const home_nav = ref(null);
const animation_card = ref(null);
const animation_close = ref(null);
const animation_fold = ref(null);
const home_banner = ref(null);

const imagesList = ref([
    {
        src: new URL(
            `../../assets/img/banner/divas-new_uvrpcj.jpg`,
            import.meta.url
        ).href,
        title: "Holiday Season Services",
        content:
            "Embrace the Bvlgari holiday spirit with iconic gifts full of magic and sparkle.",
        link: "Discover the services",
    },
    {
        src: new URL(
            `../../assets/img/banner/J-24_Xmas_Tubogas_Product01_1920x1080_belbht.jpg`,
            import.meta.url
        ).href,
        title: "Holiday Season Services",
        content:
            "Embrace the Bvlgari holiday spirit with iconic gifts full of magic and sparkle.",
        link: "Discover the services",
    },
]);
function getImageUrl(name) {
    return require(`@/assets/img/${name}`);
}
onMounted(() => {
    let timer;
    // 监听函数
    function callbackFunc(event) {
        // console.log("home_nav :>> ", home_nav.value);
        if (home_nav.value) {
            home_nav.value.parentScrollChange(event);
        }
        if (animation_card.value) {
            animation_card.value.parentScrollChange(event);
        }
        // if (animation_close.value) {
        //     animation_close.value.parentScrollChange(event);
        // }
        if (animation_fold.value) {
            animation_fold.value.parentScrollChange(event);
        }
        if (home_banner.value) {
            home_banner.value.parentScrollChange(event);
        }
    }
    // 防抖
    function resizeCallbackFunc(event) {
        clearTimeout(timer);
        timer = setTimeout(() => {
            if (home_nav.value) {
                home_nav.value.parentScrollChange(event);
            }
            if (animation_card.value) {
                animation_card.value.parentScrollChange(event);
            }
            // if (animation_close.value) {
            //     animation_close.value.parentScrollChange(event);
            // }
            if (animation_fold.value) {
                animation_fold.value.parentScrollChange(event);
            }
            if (home_banner.value) {
                home_banner.value.parentScrollChange(event);
            }
        });
    }

    // 监听滚动事件
    callbackFunc();
    window.addEventListener("resize", resizeCallbackFunc);
    home_content.value.addEventListener("scroll", callbackFunc);
});
</script>

<style scoped>
.content {
    height: 100vh;
    padding: 0px;
    margin: 0px;
    overflow: hidden;
    overflow-y: scroll;
}
</style>
