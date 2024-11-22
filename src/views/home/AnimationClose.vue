<template>
    <div class="card_close bg_fff position_relative" ref="card_close">
        <!-- <div class="inline_block w_50 position_relative h_100 bg_fff" style="z-index:4">
            <img class="img position_absolute left_box h_100" ref="left_box" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
        </div>
        <div class="inline_block position_relative w_50 h_100 bg_fff" ref="text_box" style="z-index:4">
            <div class="position_absolute right_box w_100 h_auto overflow_hidden" ref="right_box">
                <h2 class="title">Holiday Season Services</h2>
                <p class="content_text">From personalized messages to elegant gift boxes and extended returns periods, Bvlgari elevates the gesture of gift-giving to an art form with exclusive curated services designed to offer a memorable experience. </p>
                <a href="" class="link">Discover the services</a>
            </div>
        </div> -->
        <el-row>
            <el-col :xs='24' :sm='12' :lg='12'>
                <div class="h50vh">
                    <img class="img w_100 h_100" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                </div>
            </el-col>
            <el-col :xs='24' :sm='12' :lg='12'>
                <div class="h50vh position_relative">
                    <div class="fold_text left">
                        <h2 class="title">Holiday Season Services</h2>
                        <p class="content_text">Embrace the Bvlgari holiday spirit with iconic gifts full of magic and sparkle.</p>
                        <a href="" class="link">Discover the services</a>
                    </div>
                </div>
            </el-col>

            <el-col :xs='24' :sm='12' :lg='12' v-show="width">
                <div class="h50vh position_relative">
                    <div class="fold_text right">
                        <h2 class="title">Holiday Season Services</h2>
                        <p class="content_text">Embrace the Bvlgari holiday spirit with iconic gifts full of magic and sparkle.</p>
                        <a href="" class="link">Discover the services</a>
                    </div>
                </div>
            </el-col>
            <el-col :xs='24' :sm='12' :lg='12' v-show="width">
                <div class="h50vh">
                    <img class="img w_100 h_100" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                </div>
            </el-col>

            <el-col :xs='24' :sm='12' :lg='12' v-show="!width">
                <div class="h50vh">
                    <img class="img w_100 h_100" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                </div>
            </el-col>
            <el-col :xs='24' :sm='12' :lg='12' v-show="!width">
                <div class="h50vh position_relative">
                    <div class="fold_text right">
                        <h2 class="title">Holiday Season Services</h2>
                        <p class="content_text">Embrace the Bvlgari holiday spirit with iconic gifts full of magic and sparkle.</p>
                        <a href="" class="link">Discover the services</a>
                    </div>
                </div>
            </el-col>
        </el-row>
    </div>
</template>

<script setup lang="ts" name="AnimationClose">
//不需要暴露对象
import { ref } from "vue";
const card_close = ref(null);
const left_box = ref(null);
const right_box = ref(null);
const text_box = ref(null);
const width = ref(true);

const parentScrollChange = (event) => {
    // if (event) {
    //     const closeTop = card_close.value?.getBoundingClientRect().top ?? 0;
    //     const closeHeight =
    //         window.innerHeight || document.documentElement.clientHeight;
    //     const percent = closeTop / closeHeight;
    //     if (1 > percent && percent >= 0) {
    //         left_box.value.style.right =
    //             (percent < 0.2 ? 0 : percent) * 100 + "%";
    //         right_box.value.style.left =
    //             (percent < 0.2 ? 0 : percent) * 100 + "%";
    //     }
    // }
    const innerWidth =
        window.innerWidth || document.documentElement.clientWidth;
    if (innerWidth < 769) {
        width.value = false;
    } else {
        width.value = true;
    }
};
defineExpose({
    parentScrollChange,
});
</script>

<style scoped>
div {
    box-sizing: border-box;
}
.card_close {
    width: 100vw;
    z-index: 4;
}
.flex {
    display: flex;
}
.position_relative {
    position: relative;
}
.title {
    font-size: 2.25rem;
    font-weight: 300;
    line-height: 1.22;
    margin-bottom: 0.5rem;
}
.content_text {
    margin-bottom: 1.5rem;
}
.link {
    margin-top: 3.5rem;
    line-height: 1.375rem;
    padding-top: 0.625rem;
    padding-bottom: 0.625rem;
    min-height: 3rem;
    color: #000;
}
.w_50 {
    width: 50%;
}
.h_50 {
    height: 50%;
}
.h50vh {
    height: 50vh;
}
.inline_block {
    display: inline-block;
}
.img {
    width: 100%;
    object-fit: cover;
}
.position_absolute {
    position: absolute;
}
.right_box {
    transition: all 1s ease-in-out;
    margin: auto;
    top: 0px;
    bottom: 0px;
    left: 100%;
    padding: 2.5rem 5rem;
}
.left_box {
    transition: all 1s ease-in-out;
    margin: auto;
    top: 0px;
    bottom: 0px;
    right: 100%;
}
.h_100 {
    height: 100%;
}
.h_auto {
    height: fit-content;
}
.bg_fff {
    background-color: #fff !important;
}
.overflow_hidden {
    overflow: hidden;
}
.w_100 {
    width: 100%;
}
.fold_text {
    position: absolute;
    height: fit-content;
    margin: auto;
    top: 0px;
    bottom: 0px;
    padding: 2.5rem 5rem;
    width: 100%;
}
.left {
    left: 0px;
}
.right {
    right: 0px;
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
.el-col {
    height: 50%;
}
</style>
