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
                    <div class="card_square" ref="card_square_01">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                    <div class="card_square" ref="card_square_02">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                    <div class="card_square" ref="card_square_03">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script setup lang="ts" name="AnimationCard">
//不需要暴露对象
import { ref, onMounted } from "vue";

const animation_card = ref(null);
const fixed_div = ref(null);
const card_square_01 = ref(null);
const card_square_02 = ref(null);
const card_square_03 = ref(null);
const parentScrollChange = (event) => {
    // console.log("event AnimationCard:>> ", event);
    const cardTop = animation_card.value?.getBoundingClientRect().top ?? 0;
    const cardHeight =
        animation_card.value?.getBoundingClientRect().height ?? 0;
    if (event && cardTop <= 0 && cardTop >= -cardHeight) {
        fixed_div.value.style.position = "absolute";
        fixed_div.value.style.top = 0 - cardTop + "px";
        fixed_div.value.style["z-index"] = "3";
        fixed_div.value.classList.add("padding_5");
    } else {
        fixed_div.value.classList.remove("padding_5");
        fixed_div.value.style.position = "relative";
    }
    if (card_square_01) {
        const h001 = card_square_01.value?.getBoundingClientRect().width ?? 0;
        console.log("h001 :>> ", h001);

        card_square_01.value.style.height = h001 + "px";
    }
    if (card_square_02) {
        const h002 = card_square_02.value?.getBoundingClientRect().width ?? 0;
        card_square_02.value.style.height = h002 + "px";
    }
    if (card_square_03) {
        const h003 = card_square_03.value?.getBoundingClientRect().width ?? 0;
        card_square_03.value.style.height = h003 + "px";
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
    width: 100vw;
    height: 100vh;
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
    height: fit-content;
    display: flex;
    justify-content: space-between;
}
.card_square {
    height: 100px;
    width: 30%;
    overflow: hidden;
    position: relative;
}
.img {
    height: 100%;
    width: 100%;
    object-fit: cover;
}
</style>
