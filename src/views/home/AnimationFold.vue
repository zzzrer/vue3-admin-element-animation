<template>
    <div class="w_100" ref="animation_fold">
        <div class="animation_fold position_relative" ref="fold_p">
            <div class="position_relative w_100 h_100" ref="fold_fixed">
                <img class="img" src="../../assets/img/banner/J-24_Xmas_Tubogas_Product01_1920x1080_belbht.jpg" alt="">
                <div ref="box_01" class="fold_text">
                    <h2 class="title">Holiday Season Services</h2>
                    <p class="content_text">Embrace the Bvlgari holiday spirit with iconic gifts full of magic and sparkle.</p>
                    <a href="" class="link">Discover the services</a>
                </div>
            </div>
        </div>
        <div class="animation_fold position_relative">
            <div class="position_relative w_100 h_100" ref="fold_fixed_02" style="z-index:2">
                <img class="img" src="../../assets/img/banner/divas-new_uvrpcj.jpg" alt="">
                <div ref="box_02" class="fold_text">
                    <h2 class="title">Holiday Season Services</h2>
                    <p class="content_text">Embrace the Bvlgari holiday spirit with iconic gifts full of magic and sparkle.</p>
                    <a href="" class="link">Discover the services</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts" name="AnimationFold">
//不需要暴露对象
import { ref } from "vue";
const fold_fixed = ref(null);
const fold_p = ref(null);
const box_01 = ref(null);
const box_02 = ref(null);
const fold_fixed_02 = ref(null);
const animation_fold = ref(null);

const parentScrollChange = (event) => {
    const foldTop = fold_p.value?.getBoundingClientRect().top ?? 0;
    const foldHeight = fold_p.value?.getBoundingClientRect().height ?? 0;

    const showSecondTime = foldHeight - foldTop;
    console.log(
        "showSecondTime :>> ",
        showSecondTime,
        showSecondTime - foldHeight
    );
    if (event && foldTop < foldHeight && foldTop > 0) {
        fold_fixed.value.style.top = 0 + "px";
        fold_fixed.value.style.position = "relative";
        if (showSecondTime > 260) {
            box_01.value.style.top = showSecondTime - 260 + "px";
        } else {
            box_01.value.style.top = 0 + "px";
        }

        if (showSecondTime > 160) {
            fold_fixed_02.value.style.position = "absolute";
            fold_fixed_02.value.style.top =
                showSecondTime - foldHeight - 80 + "px";
        }

        animation_fold.value.style["height"] = foldHeight * 2 + "px";
    } else if (event && foldTop <= 0 && foldTop >= -foldHeight) {
        fold_fixed.value.style.position = "absolute";
        fold_fixed.value.style.top = 0 - foldTop + "px";
        fold_fixed.value.style["z-index"] = "1";

        animation_fold.value.style["height"] = foldHeight * 2 + "px";
        console.log("999999", foldTop, showSecondTime);

        if (showSecondTime > foldHeight + 260) {
            box_02.value.style.top = showSecondTime - foldHeight - 260 + "px";
        } else {
            box_02.value.style.top = "0px";
        }
    } else {
        fold_fixed_02.value.style.top = 0 + "px";
        fold_fixed_02.value.style.position = "relative";
        fold_fixed.value.style.top = 0 + "px";
        fold_fixed.value.style.position = "relative";

        animation_fold.value.style["height"] = "auto";
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
.h_100 {
    height: 100%;
}
.w_100 {
    width: 100vw;
}
.animation_fold {
    width: 100vw;
    height: 100vh;
}
.position_relative {
    position: relative;
}
.img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.fold_text {
    position: absolute;
    width: 100%;
    height: fit-content;
    top: 0px;
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
