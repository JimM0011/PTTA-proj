<script lang="ts" setup>

</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
        <el-col :xs="24" :sm="24" :md="24" :lg="24" :xl="24" class="markdown-title">
            Malicious Sample Hazards
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <p>
                Vanilla Test-Time Adaptation (TTA) algorithm treats all the test samples equally.
                However, according to the model's predictions, samples with high conditional entropy are less accurate than those with low entropy. 
                We verify the relationship between the classification accuracy and the conditional entropy of ResNet50 and ViT-B/16 pre-trained on ImageNet1K for 15 types of out-of-distribution samples in ImageNetC, as shown in Fig. 3 (top).
                **Applying Entropy Minimization (EM) for high-entropy samples does not bring benefits to TTA algorithms.
                Instead, it will undermine the stability of DNNs, especially when test data distribution has a large shift from the source training distribution.**
                As shown in Fig. 3 (down), DNNs inherently have relatively high conditional entropy for test domains with low classification accuracy.
            </p>
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12" class='img-container'>
            <img
                :src="'./malicious/acc_vs_ent.png'"
                alt="Fig. 3 (top)"
                class="img-pic"
            >
            <img
                :src="'./malicious/avg_ent.png'"
                alt="Fig. 3 (down)"
                class="img-pic"
            >
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <p>
                A simple solution is to sort the test samples (within a minibatch) in ascending order according to the conditional entropy,
                and then take the top-p% low-entropy samples, called benign samples, to apply Entropy Minimization (EM).
                This sample selection criterion can effectively improve the performance of vanilla TTA algorithm, as shown in Fig. 2. 
                **However, this success exhibits high sensitivity to thresholds (typically treated as hyperparameters) in the criterion,
                where slight variations lead to substantial performance degradation.**
                Through these observations, it is intuitive to believe that malicious samples exist in an uncertain ratio within minibatches, 
                and **existing sample selection criteria fail to completely eliminate malicious samples from test data**.
                This constitutes another form of malicious sample hazards that fundamentally constrains the practical applicability of TTA algorithms.
            </p>
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12" class='img-container'>
            <img
                :src="'./malicious/vitb16.png'"
                alt="Fig. 2 (right) ViT-B/16"
                class="img-pic-2"
            >
            <img
                :src="'./malicious/tent.png'"
                alt="Adaptation Process"
                class="img-pic-3"
            >
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

.img-pic {
    width: 65%;
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
