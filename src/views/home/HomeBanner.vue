<template>
    <div class="home_banner">
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
</script>

<style scoped>
.home_banner {
    margin-top: 40px;
    height: 106vh;
    width: 100vw;
}
.img {
    height: 100%;
    object-fit: cover;
    width: 100%;
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
