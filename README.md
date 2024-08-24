# Image Stitching for Panorama Creation

This project implements a comprehensive pipeline to stitch multiple images into a seamless panoramic image. The process involves detecting key points, extracting descriptors, matching features, estimating homography, and finally warping and blending the images.
![image](https://github.com/user-attachments/assets/fc733939-64cb-4a0e-b9c0-66b3ecdc1f0d)
![image](https://github.com/user-attachments/assets/8ac54f33-8fa5-4a6e-b972-227e02fc7446)
![image](https://github.com/user-attachments/assets/d5625371-eda7-43c9-97ce-635d8c6ea203)
![image](https://github.com/user-attachments/assets/06a21cb2-2147-469f-ba82-964327b579a2)


## Features and Implementation

1. **Key Point Detection**: Uses ORB (Oriented FAST and Rotated BRIEF) to detect key points in grayscale images.
2. **Descriptor Extraction**: Extracts descriptors for the detected key points, crucial for matching overlapping regions between images.
3. **Key Point Matching**: Matches descriptors between adjacent images using Brute-Force Matcher (BFMatcher).
4. **Homography Estimation**: Applies RANSAC to estimate homography matrices, aligning the images accurately.
5. **Image Warping and Blending**: Warps and blends images using various techniques to create the final panoramic image.

## Design and Implementation Details

- **Platform**: Google Colab
- **Tools and Libraries**: Python, OpenCV, RANSAC, ORB, Direct and Blending Mechanisms

### Steps

1. **Image Load and Conversion**: Images are loaded and converted to grayscale.
2. **Feature Detection and Visualization**: Detects and visualizes key points in images.
![image](https://github.com/user-attachments/assets/78044e96-3725-4236-a732-df770f2926fc)
3. **Feature Matching and Homography Calculation**: Matches key points and computes homography matrices.
4. **Image Warping and Blending**:
   - **Model 1 (Gradient Blending with Library Function)**: Warps and blends images using a direct library function.
   - **Model 2 (Direct Image Concatenation)**: Efficiently concatenates images with minimal color distortion.
   - **Model 3 (Gradient Blending Breakdown)**: Manually applies gradient blending for smoother transitions.
   - **Model 4 (Alpha Blending)**: Uses alpha blending for transparent overlaps but results in mixed shadows.

### Results and Performance

![image](https://github.com/user-attachments/assets/6c0694e5-11ff-4989-bcca-bbbc32f500f8)
![image](https://github.com/user-attachments/assets/c1c507e0-e135-49fb-a186-08524fd0ded6)

The results showed varying degrees of success:
- **Model 1** struggled with proper stitching.
- **Model 2** provided a clear resolution but slight color distortions.
- **Model 3** produced a good blend but required significant computational resources.
- **Model 4** resulted in overlapped images with multiple shadows.

### Conclusion

The "Direct Image Concatenation" and "Gradient Blending Breakdown Technique" were the most effective methods. Both techniques could be combined in future work to leverage the strengths of each and produce an even better panoramic output.

