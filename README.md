# FRACTAL-keras Learning UP-Sampling without High-Channel Data - Official Keras implementation 
Recommended to try out by clicking the following Colab link: https://colab.research.google.com/drive/14U3c03zLOtToGz8zNhVfPPPrcMJI3mFv?usp=sharing

Abstract

Photoacoustic computed tomography (PACT) is an emerging hybrid imaging modality with potential applications in biomedicine. A major roadblock to the widespread adoption of PACT is the limited number of detectors, which gives rise to spatial aliasing and manifests as streak artifacts in the reconstructed image. A brute-force solution to the problem is to increase the number of detectors, which, however, is often undesirable due to escalated costs. In this study, we present a novel unsupervised learning approach, inspired by fractal mathematics, to overcome this long-standing challenge. We found that small blocks of PACT channel data show self-similarity at various downsampling rates, signifying the presence of fractal characteristics. Based on this observation, a neural network trained on downsampled data can reliably perform accurate interpolation without requiring densely-sampled ground truth data, which is typically unavailable in real practice. 
![Explanation for FRACTAL](https://github.com/FangZuo123/FRACTAL-keras/blob/main/img/Figure2.jpg?raw=true)
