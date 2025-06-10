<script lang="ts" setup>
import abstract from '../mds/abstract.mdx';
import LaySummary from '../mds/laysummary.mdx';
</script>

<script lang="ts">

export default {
    data() {
        return {
            isDetailVisible: false,
        }
    },
    methods: {
        toggleDetail() {
            this.isDetailVisible = !this.isDetailVisible;
            if (this.isDetailVisible) {
                const container = document.getElementById('id-laysummary-container');
                if (container) {
                    container.style.marginBottom = '0px';
                }
            } else {
                const container = document.getElementById('id-laysummary-container');
                if (container) {
                    container.style.marginBottom = '30px';
                }
            }
        },
    },
}

</script>

<template>
  <div>
    <el-divider />
    
    <el-row justify="center" style="margin-top: 30px; margin-bottom: 20px;">
        <el-col :xs="24" :sm="18" :md="12" :lg="10" :xl="10">
            <div class="news-container">
                <div class="news-context">
                    News
                </div>
                <div class="news-content">
                    <div class="news-content-item">
                        <div class="news-content-item-time">
                            05 / 2025
                        </div>
                        <p>
                            Our paper (PTTA) has been accepted by <a href="https://icml.cc/Conferences/2025" target="_blank">ICML 2025</a>.
                        </p>
                    </div>
                </div>
            </div>
        </el-col>
    </el-row>

    <el-divider />
    
    <el-row justify="center" style="margin-top: 20px; margin-bottom: 20px;">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <p class="TLDR-text">
                <b>
                    TL;DR (Too Long; Didn't Read):
                </b>
                &nbsp;
                Rather than selecting and discarding malicious samples for test-time model adaptation, why not purify them into benign ones?
            </p>
        </el-col>
    </el-row>

    <el-row justify="center" id="id-laysummary-container" style="margin-bottom: 30px;">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <div class="paper-content-detail-button" @click="toggleDetail">
                <div v-if="!isDetailVisible" class="triangle-right"></div>
                <div v-if="isDetailVisible" class="triangle-down"></div>
                <div class="paper-content-detail-button-context">
                    Lay Summary
                </div>
            </div>
            <transition name="fade">
            <div v-if="isDetailVisible" class="paper-content-detail-container">
                <LaySummary />
            </div>
            </transition>
        </el-col>
    </el-row>

    <el-divider />

    <el-row justify="center">
        <el-col :xs="24" :sm="24" :md="24" :lg="24" :xl="24" class="abstract-title">
            Abstract
        </el-col>
        <el-col :xs="24" :sm="20" :md="12" :lg="10" :xl="10">
            <abstract />
        </el-col>
        <el-col :xs="24" :sm="20" :md="8" :lg="7" :xl="7" class="abstract-img-container">
            <img 
                :src="'./abstract.jpg'"
                alt="Pipeline"
                class="abstract-img"
            >
        </el-col>
    </el-row>
    
  </div>
</template>

<style scoped>

.abstract-img {
    width: 80%;
    margin-left: 0px;
    margin-bottom: 0px;
    margin-top: 0px;
    box-shadow: var(--el-box-shadow-light);
    border-radius: 10px;
}

.abstract-img-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

@media (max-width: 1500px) {
    .abstract-img {
        width: 100%;
        margin-left: 40px;
        margin-bottom: 0px;
        margin-top: 0px;
    }
}

@media (max-width: 992px) {
    .abstract-img {
        width: 70%;
        margin-left: 0px;
        margin-bottom: 10px;
        margin-top: 10px;
    }
}

@media (max-width: 768px) {
    .pipeline {
        width: 100%;
        margin-top: 20px;
        margin-bottom: 10px;
    }
}

@media (max-width: 576px) {
    .abstract-img {
        width: 90%;
        margin-left: 0px;
        margin-bottom: 10px;
        margin-top: 10px;
    }
}

.triangle-right {
    width: 0;
    height: 0;
    border-top: 7px solid transparent;
    border-left: 14px solid black;
    border-bottom: 7px solid transparent;
    box-sizing: border-box;
    margin-top: 1px;
}

.triangle-down {
    width: 0;
    height: 0;
    border-left: 7px solid transparent;
    border-right: 7px solid transparent;
    border-top: 14px solid black;
    box-sizing: border-box;
    margin-top: 1px;
}

.paper-content-detail-container {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    box-sizing: border-box;
    padding: 0 20px 10px 20px;
}

.paper-content-detail-button {
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    box-sizing: border-box;
}

.paper-content-detail-button-context {
    width: auto;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    font-family: "MyFont", Verdana, sans-serif;
    letter-spacing: 2px;
    font-size: 24px;
    font-weight: bold;
    text-align: center;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    unicode-bidi: isolate;
    box-sizing: border-box;
    padding-left: 16px;
    padding-right: 16px;
    cursor: pointer;
}

.news-container {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;   
}

.news-context {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-family: "MyFont", Verdana, sans-serif;
    letter-spacing: 2px;
    font-size: 24px;
    font-weight: bold;
    text-align: center;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    unicode-bidi: isolate;
    box-sizing: border-box;
    margin-bottom: 15px;
}

.news-content {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
}

.news-content-item {
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    box-sizing: border-box;
    padding-bottom: 10px;
}

.news-content-item-time {
    width: 20%;
    height: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-family: "MyFont", Verdana, sans-serif;
    background: fixed linear-gradient(to right, #f0f0f0, #d9d9d9);
    box-sizing: border-box;
    padding: 2px 0px;
    margin-right: 20px;
    margin-top: 2px;
}

.news-content-item p {
    margin: 0px;
    text-align: center;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

.abstract-title {
    font-family: "MyFont", Verdana, sans-serif;
    letter-spacing: 2px;
    font-size: 28px;
    font-weight: bold;
    text-align: center;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    unicode-bidi: isolate;
}

.TLDR-text {
    /* font-size: 18px; */
    line-height: 1.75rem;
    margin: 0px 0px 0px 0px;
}

</style>
