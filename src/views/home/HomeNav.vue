<template>
    <div class="home_nav">
        <div v-show="topSpan" class="home_top_text flex align_center justify_center">
            <div style="width:50%">
                <el-carousel motion-blur height='20px' :autoplay='false' arrow="always">
                    <el-carousel-item>
                        <div class="flex align_center justify_center">
                            <span style="width:80%;text-align:center;">
                                Bvlgari at Your Fingertips: Schedule a Virtual Appointment Today.
                            </span>
                        </div>
                    </el-carousel-item>
                    <el-carousel-item>
                        <div class="flex align_center justify_center">
                            <span style="width:80%;text-align:center;">
                                Bvlgari at Your Fingertips: Schedule a Virtual Appointment Today.
                            </span>
                        </div>
                    </el-carousel-item>
                </el-carousel>
            </div>
        </div>
        <nav class="home_top_nav flex align_center justify_between" ref="home_top_nav">
            <span>Menu</span>
            <span>BLVGARI</span>
            <span>
                <el-icon>
                    <Search />
                </el-icon>
                <el-icon>
                    <User />
                </el-icon>
                <el-icon>
                    <Goods />
                </el-icon>
            </span>
        </nav>
    </div>
</template>

<script setup lang="ts" name="HomeNav">
//不需要暴露对象
import { ref, onMounted, getCurrentInstance } from "vue";
const topSpan = ref(false);
let scroll = ref(0);
const home_top_nav = ref(null);

onMounted(() => {
    const instance = getCurrentInstance();
    const parent = instance?.parent;

    console.log("HomeNav", parent);
});
const parentScrollChange = (event) => {
    const Dom = event?.target ?? {};
    const scrollValue = Dom.scrollTop || 0;
    if (scrollValue <= scroll.value) {
        // 上滑动
        home_top_nav.value.classList.add("show_height");
        if (scrollValue === 0) {
            setTimeout(() => {
                home_top_nav.value.classList.add("hide_back");
            }, 500);
        }
    } else {
        // 下滑动
        home_top_nav.value.classList.remove("show_height");
        setTimeout(() => {
            home_top_nav.value.classList.remove("hide_back");
        }, 500);
    }
    console.log("scrollValue,scroll.value :>> ", scrollValue, scroll.value);
    scroll.value = JSON.parse(JSON.stringify(scrollValue));
    if (scrollValue === 0) {
        topSpan.value = true;
    } else {
        topSpan.value = false;
    }
};
defineExpose({
    parentScrollChange,
});
</script>

<style scoped>
.home_nav {
    z-index: 1000;
    position: fixed;
    width: 100%;
    top: 0px;
}
.hide_back {
    background: transparent !important;
    color: #fff;
}
.hide_back:hover {
    background-color: #fff !important;
    color: #000;
}
.show_height {
    height: 64px !important;
}
.home_top_text {
    height: 20px;
    padding: 10px;
    background-color: #fff;
}
.home_top_nav {
    overflow: hidden;
    height: 0px;
    padding: 0px 32px;
    background-color: #fff;
    transition: all 0.5s ease-in-out;
}
.flex {
    display: flex;
}
.align_center {
    align-items: center;
}
.justify_between {
    justify-content: space-between;
}
.justify_center {
    justify-content: center;
}
::v-deep .el-carousel__arrow {
    background: none;
    color: #000;
}
</style>

