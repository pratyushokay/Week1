# Week1
Image Processing: A Journey Through Edge Detection Techniques
1. Starting with Sobel Edge Detection
I began by applying the Sobel operator to detect edges in both horizontal (X) and vertical (Y) directions. By combining these results using weighted addition and calculating the gradient magnitude, I aimed to highlight the edges within the image.

Observations:

Without Preprocessing: The initial results were noisy and lacked clear definition. The detected edges appeared cluttered and indistinct.
Introducing Gaussian Blur: To address the noise, I applied a Gaussian Blur with a kernel size of (5,5) before edge detection. This step effectively reduced noise and smoothed the image, leading to more continuous and natural-looking edges.
Applying Thresholding: Post edge detection, I implemented binary thresholding to convert the gradient image into a clear edge map. Experimenting with different threshold values:

30: Resulted in overly broad and noisy edges, turning most of the image white.

50: Provided the most visually pleasing results with well-defined and prominent edges.

100 and above: Edges became too thin, losing several important contours.


Conclusion: A threshold value of 50 struck the optimal balance, producing clear and well-defined edges.

2. Exploring the Scharr Operator
Next, I experimented with the Scharr operator, known for its enhanced accuracy in edge detection. By combining the Scharr X and Y results through weighted addition and applying the same thresholding procedure:

Observations:

The Scharr operator yielded crisper and more defined edges compared to the Sobel operator.
A higher threshold value, around 100, resulted in sharper and clearer edges. Lower threshold values (e.g., 52) allowed moderately intense gradients to pass, leading to blurred edges.
Overall, the Scharr operator provided slightly sharper results, especially around fine details.

3. Implementing Canny Edge Detection Manually
To gain deeper insight, I manually implemented the Canny edge detection algorithm, which comprises several sequential stages:

Gaussian Blurring: Applied a Gaussian blur with a kernel size of (5,5) to smooth the image and reduce noise, ensuring prominent edges are retained.

Gradient Computation (Sobel Operator): Computed intensity gradients in the horizontal (Gx) and vertical (Gy) directions using the Sobel operator with a kernel size of 5, balancing detail detection and noise suppression.

Gradient Magnitude and Direction: Calculated the overall edge strength and orientation at each pixel, normalizing the magnitude to the 0-255 range for consistency.

Non-Maximum Suppression (NMS): Thinned out detected edges by preserving only local maxima along the gradient direction. This involved mapping gradient directions to one of four main angles (0°, 45°, 90°, 135°) and comparing each pixel’s magnitude with its neighbors along the gradient direction.

Double Thresholding: Classified edge pixels into strong, weak, or non-relevant based on magnitude. Chosen threshold values were:

lowThreshold = 5

highThreshold = 10

These lower values aimed to capture finer edge details while still retaining strong edges, as higher thresholds previously excluded subtle but meaningful edges.

Edge Tracking by Hysteresis: Finalized edges by retaining weak pixels connected to strong pixels and discarding isolated weak pixels. This involved iterating through weak pixels and promoting them to strong if connected to a strong pixel (8-connectivity); otherwise, they were suppressed.

This comprehensive approach allowed for a deeper understanding of edge detection techniques and their impact on image processing outcomes.

