# FRACTAL-keras Learning UP-Sampling without High-Channel Data - Official Keras implementation 

Recommended to try out by clicking the following Colab link: https://colab.research.google.com/drive/14U3c03zLOtToGz8zNhVfPPPrcMJI3mFv?usp=sharing

## Abstract

Photoacoustic computed tomography (PACT) is an emerging hybrid imaging modality with potential applications in biomedicine. A major roadblock to the widespread adoption of PACT is the limited number of detectors, which gives rise to spatial aliasing and manifests as streak artifacts in the reconstructed image. A brute-force solution to the problem is to increase the number of detectors, which, however, is often undesirable due to escalated costs. In this study, we present a novel unsupervised learning approach, inspired by fractal mathematics, to overcome this long-standing challenge. We found that small blocks of PACT channel data show self-similarity at various downsampling rates, signifying the presence of fractal characteristics. Based on this observation, a neural network trained on downsampled data can reliably perform accurate interpolation without requiring densely-sampled ground truth data, which is typically unavailable in real practice. 
![Explanation for FRACTAL](https://github.com/FangZuo123/FRACTAL-keras/blob/main/img/Figure2.jpg?raw=true)
Figure 1. Self-similarity in PACT data bears resemblance to a fractal characteristic. a. The Koch curve shows a pattern with fractal characteristics. b. PACT sinograms showing self-similarity across different scales.   

## Resources

All the material, including source code, is made freely available for non-commercial use under the MIT license. Feel free to use any of the material in your own work, as long as you give us appropriate credit by mentioning the title and author list of our paper.

## Getting started

The below sections detail how to get set up for training the FRACTAL network using the dataset we provided. 

### Dependencies

Keras >= 2.8, TensorFlow>= 2.8, NumPy, OpenCV

### Training networks

To train the FRACTAL network:

`python train.py --image_dir phantom --test_dir animal_256 --image_size 64 --batch_size 8 --lr 0.001 --output_path phantom_unet_128 --model unet`

The detailed options are:

```
optional arguments:
  -h, --help            show this help message and exit
  --image_dir  IMAGE_DIR
                        train image dir

  --test_dir   TEST_DIR
                        test image dir (default: None)

  --weight_file WEIGHT_FILE
                        trained weight file (default: None)
  --image_size IMAGE_SIZE
                        patch size during training(default: 64)
  --batch_size BATCH_SIZE
                        --batch_size 8
  --output_dir OUTPUT_DIR
                        save the trained network weights.
  --model MODEL         model architecture ('srresnet' or 'unet') (default:
                        srresnet)

```



### Validation using a trained network

Once you've trained a network, you can run a validation dataset through the network:

`python test_model.py --weight_file /content/FRACTAL-keras/phantom_unet_128/phantom_unet.hdf5 --image_dir animal_128 --output_dir sinogram_enlarge2/ --enlargement_factor 2 --model unet`


```
optional arguments:
  -h, --help            show this help message and exit
  --weight_file WEIGHT_FILE
                        trained network weight file
  --image_dir  IMAGE_DIR
                        test image dir
  --output_dir OUTPUT_DIR
                        if set, save resulting images otherwise show result
                        using imshow (default: None)
  --enlargement_factor ENLARGEMENT_FACTOR
                        N Multiplies the number of output channels by 2^N (default: 2).
  --model MODEL         model architecture ('srresnet' or 'unet') (default:
                        srresnet)                        

```

### Enlargement Factor

Adjusting the enlargement factor alters the number of output channels in the channel data. If the enlargement factor is N, then the number of output channels will be 2^N times the original. This adjustment is independent of the channel count used during training, and N can be varied freely to allow interpolation.

### Pre-trained networks

Here we provides a pre-trained U-Net model trained by a ring-array PACT system.

[model_unet_phantom.hdf5](https://drive.google.com/file/d/1Kp4gcmioyspY2X7lQbDqdtry0zmvy_sB/view?usp=share_link)

If this pre-trained model doesn't meet your specific needs, you are encouraged to train your own model. Feel free to use this as a starting point for your custom solutions.

## Other

The dataset provided here allows for a simple and stable replication of the fractal results presented in my paper. Should you require any additional data from my publication, or if you encounter difficulties while training with your own data, please do not hesitate to reach out to me.

Contact: dkx17@mails.tsinghua.edu.cn

## Acknowledgements

This project utilizes code from [yu4u's noise2noise repository](https://github.com/yu4u/noise2noise), which is licensed under the MIT License. I extend my heartfelt thanks to the original author for their valuable work, which greatly contributed to the development of this project.
