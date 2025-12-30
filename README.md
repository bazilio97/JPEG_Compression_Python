Image Compression and Reconstruction Using DCT
=============================================

WARNING: THIS SCRIPT CAN BE ONLY USED FOR GRAYSCALE IMAGES !!!

This project implements image compression and reconstruction using the Discrete Cosine Transform (DCT) in Python. 
The workflow includes splitting the image into blocks, applying forward DCT, quantization, dequantization, 
and inverse DCT to reconstruct the image.

Workflow Overview
-----------------

1. Reading and Displaying the Image
----------------------------------
- The image is loaded using PIL's Image module.
- The image is displayed using matplotlib for quality comparison before compression.

2. Splitting the Image into Blocks
----------------------------------
- Function: matsplitter(matrix, N, M)
- Splits the image pixel matrix into submatrices (blocks) of size 8 x 8.
- Purpose: Process each block separately for DCT.

3. Forward Discrete Cosine Transform (DCT)
------------------------------------------
- Function: fDCT(mBlock)
- Applies forward DCT to each 8x8 block.
- Converts spatial pixel values into frequency domain coefficients.

4. Quantization
---------------
- Standard quantization table for quality 20% `q20` is used to reduce high-frequency details.
- Each DCT coefficient is divided by the corresponding quantization value and rounded.
- Purpose: Compression by reducing the amount of data needed to store the image.

5. Dequantization
-----------------
- Each quantized DCT block is multiplied back by the quantization table.
- Prepares the block for reconstruction using inverse DCT.

6. Inverse DCT
--------------
- Function: iDCT(mBlock)
- Converts frequency domain coefficients back into spatial pixel values.
- Reconstructs the original image from the processed DCT blocks.

7. Joining Blocks
-----------------
- Function: matjoin(blocks, original_shape, N, M)
- Combines all 8x8 blocks back into the full image matrix.

8. Displaying the Reconstructed Image
-------------------------------------
- The reconstructed image is displayed using matplotlib.
- Allows visual comparison of the compression effect.


Notes
-----
- The quantization table `q20` corresponds to an approximate quality factor of 20%.
- This implementation is suitable for grayscale images; color images would require separate processing per channel.

Usage
-----
1. Set the path to your input image:
   img = Image.open("/path/to/your/image.jpg")
2. Run the script.
3. Compare the original and reconstructed images displayed using matplotlib.
