# Cartoonify-Image-Processing-Project
Developed a python program to convert an image into a cartoon version of it using image processing techniques..

Here in our project we have majorly made use of the cv2 library.
cv2 is an open source library which is very useful for computer vision applications such as video
analysis, CCTV footage analysis and image analysis.
The first step of cartoonifying the image is to convert the original image to a grey scale image.
Next, we use a median blur filter to smoothen the image. Here we have used the median filter as, the
median value must actually be the value of one of the pixels in the neighborhood, the median filter
does not create new unrealistic pixel values when the filter straddles an edge. For this reason the
median filter is much better at preserving sharp edges than the mean filter.
cv2.medianBlur - The medianBlur operation is similar to the other averaging methods. Here, the
central element of the image is replaced by the median of all the pixels in the kernel area. This
operation processes the edges while removing the noise.
After applying the median blur filter we apply adaptive thresholding on the filtered image.
cv2.adaptiveThreshold - adaptive thresholding considers a small set of neighboring pixels at a time,
computes threshold for that specific local region, and then performs the segmentation. Syntax:
cv2.adaptiveThreshold(src, maxValue, adaptiveMethod, thresholdType, blockSize, C). Where using the
adaptiveMethod the threshold value = (Mean of the neighbourhood area values – constant value) is
found. In other words, it is the mean of the blockSize×blockSize neighborhood of a point minus
constant(C). So, larger the block size thicker the edges.
We now apply bilateral filter on the original image to smoothen it and reduce noise.
cv2.bilateralFilter - A bilateral filter is a non-linear, edge-preserving, and noise-reducing smoothing
filter for images. It replaces the intensity of each pixel with a weighted average of intensity values
from nearby pixels. This weight can be based on a Gaussian distribution. It ensures that only those
pixels with intensity values similar to that of the central pixel are considered for blurring, while sharp
intensity changes are maintained.
The image smoothened using bilateral filter is masked with the image where edges were found.
A mask is a binary image consisting of zero- and non-zero values. If a mask is applied to another
binary or to a grayscale image of the same size, all pixels which are zero in the mask are set to zero in
the output image. All others remain unchanged.
cv2.bitwise_and - Bitwise operations are used in image manipulation and used for extracting
essential parts in the image. In bitwise_and the logical AND operation is performed. Also, Bitwise
operations helps in image masking.
Thus, we get our cartoonified image
