<template>
    <div class="home_banner" ref="home_banner">
        <el-carousel motion-blur height='106vh'>
            <el-carousel-item v-for="(item,index) in showList" :key="'banner_' + index">
                <div>
                    <img :src="item.src" alt="加载中...." class="img" style="" />
                    <div class="fold_text">
                        <h2 class="title">Holiday Season Services</h2>
                        <p class="content_text">Embrace the Bvlgari holiday spirit with iconic gifts full of magic and sparkle.</p>
                        <a href="" class="link">Discover the services</a>
                    </div>
                </div>
            </el-carousel-item>
        </el-carousel>
        <div class="overlay" ref="overlay">19999999999999</div>
    </div>
</template>

<script setup lang="ts" name="HomeBanner">
//不需要暴露对象
import { ref } from "vue";
const a = ref(0);
const props = defineProps({
    showList: {
        type: Array,
        default: () => [],
    },
});
const overlay = ref(null);
const parentScrollChange = (event) => {
    if (event && overlay) {
        const overlayTop = overlay.value.getBoundingClientRect().top;
        const overlayHeight = overlay.value.getBoundingClientRect().height;
        const half = overlayHeight / 3;
        if (overlayTop * -1 > half) {
            const percent = (overlayTop * -1) / overlayHeight;
            console.log("percent :>> ", percent);
            if (percent > 0 && percent <= 0.25) {
                overlay.value.classList.remove("opacity_50");
                overlay.value.classList.remove("opacity_75");
                overlay.value.classList.remove("opacity_100");
                overlay.value.classList.add("opacity_25");
            } else if (percent > 0.25 && percent <= 0.5) {
                overlay.value.classList.remove("opacity_25");
                overlay.value.classList.remove("opacity_75");
                overlay.value.classList.remove("opacity_100");
                overlay.value.classList.add("opacity_50");
            } else if (percent > 0.5 && percent <= 0.75) {
                overlay.value.classList.remove("opacity_25");
                overlay.value.classList.remove("opacity_50");
                overlay.value.classList.remove("opacity_100");
                overlay.value.classList.add("opacity_75");
            } else if (percent > 0.75 && percent <= 1) {
                overlay.value.classList.remove("opacity_25");
                overlay.value.classList.remove("opacity_50");
                overlay.value.classList.remove("opacity_75");
                overlay.value.classList.add("opacity_100");
            }
        } else {
            overlay.value.classList.remove("opacity_25");
            overlay.value.classList.remove("opacity_50");
            overlay.value.classList.remove("opacity_75");
            overlay.value.classList.remove("opacity_100");
        }
    } else {
    }
};
defineExpose({
    parentScrollChange,
});
</script>

<style scoped>
.home_banner {
    margin-top: 40px;
    height: 106vh;
    width: 100vw;
    position: relative;
}
.img {
    height: 100%;
    object-fit: cover;
    width: 100%;
}
.overlay {
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0px;
    left: 0px;
    background-color: #fff;
    transition: all 1s ease-in-out;
    opacity: 0;
}
.opacity_25 {
    opacity: 0.25;
}
.opacity_50 {
    opacity: 0.5;
}
.opacity_75 {
    opacity: 0.75;
}
.opacity_100 {
    opacity: 1;
}
.fold_text {
    position: absolute;
    width: 100%;
    height: fit-content;
    bottom: 6vh;
    padding: 2.5rem 5rem;
    width: 50%;
    left: 0px;
}
.fold_text h2 {
    font-size: 2.25rem;
    font-weight: 300;
    line-height: 1.22;
    margin-bottom: 0.5rem;
}
.fold_text p {
    margin-bottom: 1.5rem;
}
.fold_text a {
    margin-top: 3.5rem;
    line-height: 1.375rem;
    padding-top: 0.625rem;
    padding-bottom: 0.625rem;
    min-height: 3rem;
    color: #000;
}
</style>
