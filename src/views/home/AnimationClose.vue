<template>
    <div class="card_close bg_fff" ref="card_close">
        <div class="inline_block w_50 position_relative h_100 bg_fff" style="z-index:4">
            <img class="img position_absolute left_box h_100" ref="left_box" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
        </div>
        <div class="inline_block position_relative w_50 h_100 bg_fff" style="z-index:4">
            <div class="position_absolute right_box w_100 h_auto overflow_hidden" ref="right_box">
                <h2 class="title">Holiday Season Services</h2>
                <p class="content_text">From personalized messages to elegant gift boxes and extended returns periods, Bvlgari elevates the gesture of gift-giving to an art form with exclusive curated services designed to offer a memorable experience. </p>
                <a href="" class="link">Discover the services</a>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts" name="AnimationClose">
//不需要暴露对象
import { ref } from "vue";
const card_close = ref(null);
const left_box = ref(null);
const right_box = ref(null);

const parentScrollChange = (event) => {
    if (event) {
        const closeTop = card_close.value?.getBoundingClientRect().top ?? 0;
        const closeHeight =
            window.innerHeight || document.documentElement.clientHeight;
        const percent = closeTop / closeHeight;
        if (1 > percent && percent >= 0) {
            left_box.value.style.right =
                (percent < 0.2 ? 0 : percent) * 100 + "%";
            right_box.value.style.left =
                (percent < 0.2 ? 0 : percent) * 100 + "%";
        }
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
    height: 100vh;
    width: 100vw;
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
.inline_block {
    display: inline-block;
}
.img {
    width: 100%;
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
</style>
