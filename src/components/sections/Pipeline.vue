<script lang="ts" setup>
import M1 from '../mds/pipeline.mdx';
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
        <el-col :xs="24" :sm="24" :md="24" :lg="24" :xl="24" class="markdown-title">
            Solution: PTTA
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <img
                :src="'./pipeline.jpg'"
                alt="Pipeline"
                class="img-pipeline"
            >
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <M1/>
        </el-col>
    </el-row>

  </div>
</template>

<style scoped>

.img-pic-2 {
    width: 40%;
}

.img-pic-3 {
    width: 100%;
}

.img-pipeline {
    width: 100%;
    margin-bottom: 2px;
    margin-top: 2px;
}

@media (max-width: 1500px) {
    .img-pic {
        width: 80%;
        margin-bottom: 5px;
        margin-top: 5px;
    }
    .img-pic-2 {
        width: 60%;
    }
}

@media (max-width: 992px) {
    .img-pic {
        width: 70%;
        margin-bottom: 5px;
        margin-top: 5px;
    }
    .img-pic-2 {
        width: 30%;
    }
}

@media (max-width: 576px) {
    .img-pic {
        width: 90%;
        margin-bottom: 5px;
        margin-top: 5px;
    }
    .img-pic-2 {
        width: 45%;
    }
}

.img-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    /* box-shadow: var(--el-box-shadow-light); */
}

.markdown-title {
    font-family: "MyFont", Verdana, sans-serif;
    letter-spacing: 2px;
    font-size: 28px;
    font-weight: bold;
    text-align: center;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    unicode-bidi: isolate;
}

</style>
