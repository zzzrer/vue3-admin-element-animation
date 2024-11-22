<template>
    <div class="animation_card" ref="animation_card">
        <div style="padding:0px 1rem;" class="fixed_div" ref="fixed_div">
            <el-row>
                <el-col :xs='24' :sm='8' :lg='8'>
                    <div class="card" ref="card_01">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                </el-col>
                <el-col :xs='24' :sm='16' :lg='16'>
                    <div class="card" ref="card_02">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                </el-col>
                <el-col :xs='24' :sm='8' :lg='8'>
                    <div class="card_square" ref="card_square_01">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                </el-col>
                <el-col :xs='24' :sm='8' :lg='8'>
                    <div class="card_square" ref="card_square_02">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                </el-col>
                <el-col :xs='24' :sm='8' :lg='8'>
                    <div class="card_square" ref="card_square_03">
                        <img class="img" src="../../assets/img/a-24-xmas-serpenti-product02-1080x1080.jpg" alt="">
                    </div>
                </el-col>
            </el-row>
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
const card_01 = ref(null);
const card_02 = ref(null);

const parentScrollChange = (event) => {
    // console.log("event AnimationCard:>> ", event);
    // const cardTop = animation_card.value?.getBoundingClientRect().top ?? 0;

    // const cardHeight =
    //     animation_card.value?.getBoundingClientRect().height ?? 0;
    // if (event && cardTop <= 0 && cardTop >= -cardHeight) {
    //     animation_card.value.style.height = cardHeight + "px";

    //     fixed_div.value.style.position = "absolute";
    //     fixed_div.value.style['top'] = 0 - cardTop + "px";
    //     fixed_div.value.style["z-index"] = "3";
    // } else {
    //     fixed_div.value.style.position = "relative";
    //     fixed_div.value.style.removeProperty("top");
    //     animation_card.value.style.removeProperty("height");
    // }
    const innerWidth =
        window.innerWidth || document.documentElement.clientWidth;
    if (innerWidth < 769) {
        card_02.value.classList.add("padding_p");
        card_01.value.classList.add("padding_p");
        card_square_01.value.classList.add("padding_p");
        card_square_02.value.classList.add("padding_p");
        card_square_03.value.classList.add("padding_p");
    } else {
        card_02.value.classList.remove("padding_p");
        card_01.value.classList.remove("padding_p");
        card_square_01.value.classList.remove("padding_p");
        card_square_02.value.classList.remove("padding_p");
        card_square_03.value.classList.remove("padding_p");
    }

    const h001 = card_square_01.value?.getBoundingClientRect().width ?? 0;
    if (card_02) {
        card_02.value.style.height = h001 + "px";
    }
    if (card_01) {
        card_01.value.style.height = h001 + "px";
    }

    if (card_square_01) {
        card_square_01.value.style.height = h001 + "px";
    }
    if (card_square_02) {
        card_square_02.value.style.height = h001 + "px";
    }
    if (card_square_03) {
        card_square_03.value.style.height = h001 + "px";
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
    position: relative;
}
.card {
    overflow: hidden;
    position: relative;
    padding: 4rem 2rem 2rem 2rem;
}
.fixed_div {
    width: 100%;
    height: 100%;
    left: 0px;
}
.padding_p {
    padding: 1.5rem !important;
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
    overflow: hidden;
    position: relative;
    padding: 2rem 2rem 4rem 2rem;
}
.img {
    height: 100%;
    width: 100%;
    object-fit: cover;
    box-shadow: -4px 4px 8px rgba(0, 0, 0, 0.2),
        /* 内层阴影 */ -12px 12px 16px rgba(0, 0, 0, 0.5); /* 外层阴影 */
}
</style>
