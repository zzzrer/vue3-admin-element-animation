<template>
    <div class="animation_card" ref="animation_card">
        <div class="fixed_div" ref="fixed_div">
            <div class="flex flex_column h-100">
                <div class="img_div_1">
                    <div class="card">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                    <div class="card">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                </div>
                <div class="img_div_2">
                    <div class="card_square">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                    <div class="card_square">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                    <div class="card_square">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script setup lang="ts" name="AnimationCard">
//不需要暴露对象
import { ref } from "vue";
const isResizeH = ref(false);
const animation_card = ref(null);
const fixed_div = ref(null);
const parentScrollChange = (event) => {
    // console.log("event AnimationCard:>> ", event);
    const top = animation_card.value?.getBoundingClientRect().top ?? 0;
    const height = animation_card.value?.getBoundingClientRect().height ?? 0;
    if (event && top <= 0 && top >= -height) {
        if (!isResizeH.value) {
            isResizeH.value = true;
            animation_card.value.style.height = height + "px";
        }
        fixed_div.value.style.position = "absolute";
        fixed_div.value.style.top = 0 - top + "px";
        fixed_div.value.style["z-index"] = "-1";
        fixed_div.value.classList.add("padding_5");
    } else {
        fixed_div.value.classList.remove("padding_5");
        fixed_div.value.style.position = "relative";
        animation_card.value.classList.remove("fixed");
        isResizeH.value = false;
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
.animation_card {
    width: 100%;
    height: 100%;
    padding: 5rem;
    position: relative;
}
.card {
    height: 100%;
    overflow: hidden;
    position: relative;
}
.fixed_div {
    width: 100%;
    height: 100%;
    left: 0px;
}
.padding_5 {
    padding: 5rem;
}
.flex {
    display: flex;
}
.flex_column {
    flex-direction: column;
}
.h-100 {
    height: 100%;
}
.fixed_div .img_div_1 {
    flex-grow: 1;
    min-height: 0;
    display: flex;
    margin-bottom: 2.5rem;
    justify-content: space-between;
}
.img_div_1 div:nth-child(odd) {
    width: 40%;
}
.img_div_1 div:nth-child(even) {
    width: 55%;
}
.img_div_2 {
    height: 350px;
    display: flex;
    justify-content: space-between;
}
.card_square {
    height: 350px;
    width: 350px;
    overflow: hidden;
    position: relative;
}
.img {
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0px;
    left: 0px;
}
</style>
