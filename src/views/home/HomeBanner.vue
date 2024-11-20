<template>
    <div class="home_banner">
        <el-carousel motion-blur autoplay height='110vh'>
            <el-carousel-item v-for="(item,index) in showList" :key="'banner_' + index">
                <img :src="item.src" alt="加载中...." style="height:100%" />
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
    height: 110vh;
    width: 100vw;
}
</style>
