<template>
    <div class="login_span">
        <div :style="{width:is769?'100%':'70%'}">
            <el-row>
                <el-col :xs='24' :sm='12'>
                    <h2 style="font-size:2.25rem;margin-bottom:1rem">Join the Bvlgari Universe</h2>
                    <p style="font-size:1.25rem">Discover its magnificent icons, personalized services and unique experiences</p>
                </el-col>
                <el-col :xs='24' :sm='12'>
                    <div class="button_p">
                        <button class="button">LOGIN UP</button>
                    </div>
                </el-col>
            </el-row>
        </div>
    </div>
</template>

<script setup lang="ts" name="LoginSpan">
//不需要暴露对象
import { ref } from "vue";
const is769 = ref(true);
const parentScrollChange = (event) => {
    const innerWidth =
        window.innerWidth || document.documentElement.clientWidth;
    if (innerWidth < 769) {
        is769.value = true;
    } else {
        is769.value = false;
    }
};
defineExpose({
    parentScrollChange,
});
</script>

<style scoped>
.login_span {
    padding: 3.75rem 0rem;
    display: flex;
    justify-content: center;
    align-items: center;
}
.button {
    line-height: 1.375rem;
    font-size: 1rem;
    padding-top: 0.625rem;
    padding-bottom: 0.625rem;
    min-height: 3rem;
    margin-top: 0px;
}
.button_p{
    width: 100%;
    height: 100%;
    display: flex;
    justify-self: flex-start;
    align-items: flex-end;
}
</style>
