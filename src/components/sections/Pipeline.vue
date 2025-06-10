<script lang="ts">

import { defineComponent } from 'vue'
import { VueLatex } from 'vatex'

export default defineComponent({
  components: {
    VueLatex
  }
})

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
            <p>
                The pipeline of <b>Purification for Test-Time Adaptation (PTTA)</b>.
                We purify malicious test samples using benign samples retrieved from a memory bank or within the mini-batch, 
                based on the saliency indicator we proposed for encoding benign and malicious data. 
                The purified samples are used to calculate the purification loss 
                <VueLatex expression="\mathcal{L}_{\text{pur}}" />, 
                which is directly inserted into the original objective function 
                <VueLatex expression="\mathcal{L}_{\text{tta}}" /> of existing TTA methods.
            </p>
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
            <h3>1. Saliency Indicator</h3>

            <p>
                We introduce an indicator for encoding benign and malicious samples.
            </p>

            <p>
                <b>Logit-saliency indicator</b> employs <VueLatex expression="\nabla_z \mathcal{L}_{\text{Ent}}" /> as the saliency information.
                <VueLatex expression="\nabla_z \mathcal{L}_{\text{Ent}}" /> is directly calculated without the need of backpropagating gradients,
                <i>i.e.</i>,
            </p>

            <p>
                <VueLatex expression="
                    \nabla_z \mathcal{L}_{\text{Ent}}(f_\theta(x)) = - ( \mathbf{z} - \mathbf{p} \cdot \mathbf{z}) \odot \mathbf{p},
                " display-mode />
            </p>

            <p>
                where <VueLatex expression="f_\theta" /> is a model (DNN) with parameters <VueLatex expression="\theta" />,
                <VueLatex expression="x" /> is an input sample,
                <VueLatex expression="\mathcal{L}_{\text{Ent}}" /> is the Entropy Minimization (EM) objective (loss) function,
                <VueLatex expression="\mathbf{z}" /> is the output logits of the model,
                and <VueLatex expression="\mathbf{p}" /> is the softmax probabilities of the logits.
            </p>

            <p>
                Intuitively, the logit-level saliency represents the changes in the logits <VueLatex expression="\mathbf{z}" />  output of the model after optimization 
                with respect to the sample <VueLatex expression="x" />.
                It directly encodes the impact of test samples on the model's final decisions.
            </p>

            <p>
                <b>Saliency distance:</b>
                The unit vector of logit-level saliency indicates the direction in which the entropy of model's predictions decreases the fastest.
                The directions corresponding to benign samples <VueLatex expression="x^+" /> and malicious samples <VueLatex expression="x^-" /> are opposite to each other.
                Therefore, a good saliency indicator satisfies <VueLatex expression="\mathcal{D}_{sa}(x^+,x^+) > \mathcal{D}_{sa}(x^+,x^-) > \mathcal{D}_{sa}(x^-,x^-)" />,
                where <VueLatex expression="\mathcal{D}_{sa}" /> is the saliency distance:
            </p>

            <p>
                <VueLatex expression="
                    \mathcal{D}_{sa} = 1 - \text{Cosine} (\nabla_x\mathcal{L}_{\text{Ent}}(f_\theta(x_i)),\ \nabla_x\mathcal{L}_{\text{Ent}}(f_\theta(x_j))).
                " display-mode />
            </p>

            <p>
                We compare the saliency distance 
                (normalized to the range of <VueLatex expression="0 \sim 1" />) among test samples 
                sorted in the ascending order of prediction entropy and split by percentages.
            </p>
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <img
                :src="'./saliency/logit.png'"
                alt="Logit Saliency"
                class="img-saliency"
            >
            <img
                :src="'./saliency/feature.png'"
                alt="Feature Saliency"
                class="img-saliency"
            >
            <img
                :src="'./saliency/image.png'"
                alt="Image Saliency"
                class="img-saliency"
            >
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col 
            :xs="24" :sm="20" :md="16" :lg="12" :xl="12"
            style="display: flex; flex-direction: row; align-items: center; justify-content: center;"
        >
            <div style="width: 33%; text-align: center;">
                <b>Logit-Saliency Indicator</b>
            </div>
            <div style="width: 33%; text-align: center;">
                Feature-Saliency Indicator
            </div>
            <div style="width: 33%; text-align: center;">
                Pixel-Saliency Indicator
            </div>
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <h3>2. Benign Sample Retrieval</h3>
        </el-col>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <h3>3. Malicious Sample Purification</h3>

        </el-col>
    </el-row>

  </div>
</template>

<style scoped>

.img-pipeline {
    width: 100%;
    margin-bottom: 2px;
    margin-top: 2px;
}

.img-saliency {
    width: 32%;
    margin: 3px;
}

@media (max-width: 1500px) {
    
}

@media (max-width: 992px) {
    
}

@media (max-width: 576px) {
    
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
