<template>
    <div class="footer">
        <div class="footer_link">
            <div class="footer_logo">BVLOARI</div>

            <el-row>
                <el-col :xs='12' :sm='6' :lg='6'>
                    <h3 class="footer_title">
                        Contact Hub
                    </h3>
                    <ul class="footer_ul">
                        <li>Store locator</li>
                        <li>Contact us</li>
                        <li>Book an appointment</li>
                    </ul>
                </el-col>
                <el-col :xs='12' :sm='6' :lg='6'>
                    <h3 class="footer_title">
                        Contact Hub
                    </h3>
                    <ul class="footer_ul">
                        <li>Store locator</li>
                        <li>Contact us</li>
                        <li>Book an appointment</li>
                        <li>Book an appointment</li>
                        <li>Book an appointment</li>
                    </ul>
                </el-col>
                <el-col :xs='12' :sm='6' :lg='6'>
                    <h3 class="footer_title">
                        Contact Hub
                    </h3>
                    <ul class="footer_ul">
                        <li>Store locator</li>
                        <li>Contact us</li>
                        <li>Contact us</li>
                        <li>Contact us</li>
                        <li>Book an appointment</li>
                    </ul>
                </el-col>
                <el-col :xs='12' :sm='6' :lg='6'>
                    <h3 class="footer_title">
                        Contact Hub
                    </h3>
                    <ul class="footer_ul">
                        <li>Store locator</li>
                        <li>Store locator</li>
                        <li>Contact us</li>
                        <li>Book an appointment</li>
                    </ul>
                </el-col>
            </el-row>
        </div>

        <div class="footer_line">
            <div>
                Change Country/Region United States
            </div>
            <div>
                ©XXX公司 京ICP证000000000000号 京ICP备00000000000号<a href="https://beian.mps.gov.cn/">京公网安备 000000000000000号</a>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts" name="FooterTemp">
//不需要暴露对象
import { ref } from "vue";
const a = ref(0);
</script>

<style scoped>
div {
    box-sizing: border-box;
}

.footer {
    width: 100vw;
    background-color: #f3f2f3;
}
.footer_link {
    padding: 40px;
}
.footer_logo {
    text-align: center;
    font-size: 3rem;
    letter-spacing: 1rem;
    padding-bottom: 40px;
}
.footer_line {
    width: 100%;
    background-color: #aaa;
    display: flex;
    flex-direction: column;
}
.footer_line div:nth-child(odd) {
    padding: 40px 40px 20px 40px;
    font-size: 0.875rem;
    font-weight: 400;
    background-color: #f3f2f3;
    border-bottom: 1px solid #aaa;
}
.footer_line div:nth-child(even) {
    padding: 20px 40px 40px 40px;
    font-size: 0.875rem;
    font-weight: 400;
    background-color: #f3f2f3;
}
.footer_ul li {
    list-style: none;
    font-size: 1rem;
    font-weight: 400;
    padding: 0.5rem;
}
.footer_title {
    padding: 0.5rem 0.5rem 1rem 0.5rem;
}
</style>
