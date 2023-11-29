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
                        training image dir

  --test_dir   TEST_DIR
                        test image dir (default: None)

  --model MODEL         model architecture ('srresnet' or 'unet') (default:
                        srresnet)
  --weight_file WEIGHT_FILE
                        trained weight file (default: None)
  --image_size IMAGE_SIZE
                        patch size during training(default: 64)
  --batch_size BATCH_SIZE
                        --batch_size 8
  --output_dir OUTPUT_DIR
                        if set, save resulting images otherwise show result
                        using imshow (default: None)

```

### Validation using a trained network

Once you've trained a network, you can run a validation dataset through the network:

`python test_model.py --weight_file /content/FRACTAL-keras/phantom_unet_128/phantom_unet.hdf5 --image_dir animal_128 --output_dir sinogram_enlarge2/ --enlargement_factor 2 --model unet`


### Pre-trained networks

You can find pre-trained networks for ring-array system here: 
[https://drive.google.com/drive/folders/1-84ORv4wB8W3M6WngFTtccuW7SlPku0V](https://drive.google.com/file/d/1Kp4gcmioyspY2X7lQbDqdtry0zmvy_sB/view?usp=share_link)https://drive.google.com/file/d/1Kp4gcmioyspY2X7lQbDqdtry0zmvy_sB/view?usp=share_link

## Other


The dataset provided here ensures a simple and stable replication of the FRACTAL results. If you need any other data from my paper, feel free to contact me.

dkx17@mails.tsinghua.edu.cn
