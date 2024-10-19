# SRResNet: Super-Resolution Residual Network

**SRResNet** (Super-Resolution Residual Network) is a deep learning model for single-image super-resolution, introduced by Ledig et al. in the 2017 paper *"Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network"*. This model is designed to enhance the resolution of low-resolution (LR) images and generate high-resolution (HR) images by leveraging deep residual networks.

## Key Components of SRResNet

1. **Input Convolution Layer**:
   - Extracts features from the low-resolution input image.
   - Applies a convolution operation to produce feature maps.
   
2. **Residual Blocks**:
   - A stack of residual blocks, where each block has:
     - Two convolutional layers with batch normalization.
     - ReLU activation function.
     - Skip connection that adds input to the output, helping gradients flow and improving learning efficiency.

3. **Upsampling Blocks**:
   - After passing through residual blocks, feature maps are upsampled using sub-pixel convolution.
   - This helps increase the spatial resolution of the image.
   
4. **Output Convolution Layer**:
   - Produces the final high-resolution image using a convolutional operation.
   - The final activation function is `tanh` to constrain pixel values between -1 and 1.
