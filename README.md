# Image-White-Balancing

This code provides two different approaches for white balancing images: the Gray-world algorithm and the White patch reference method.

## Gray-world algorithm

The Gray-world algorithm assumes that the average pixel value in an image is neutral gray (128) due to a good distribution of colors. This approach estimates the pixel color by calculating the average color. Here's how it works:

1. Convert the image to the LAB color space, where L represents lightness, A represents Red/Green, and B represents Blue/Yellow.
2. Calculate the mean color values in the A and B channels.
3. Subtract 128 (mid gray) from the means and normalize the L channel by multiplying it with this difference.
4. Subtract the resulting value from the A and B channels.
5. Optionally, you can add a multiplication factor to adjust the overall brightness of each A or B channel.

To use this approach, you can call the `GW_white_balance()` function with an input image. It will return the white-balanced image.

## White patch reference

The White patch reference method involves selecting a patch of the image that is supposed to be white and using it as a reference to rescale each channel in the image. The following steps outline the process:

1. Display the image and allow the user to click on it to select a point.
2. Capture the coordinates of the clicked point and display them.
3. Capture the color values (B, G, R) of the clicked point and display them.
4. Define a patch around the region that is supposed to be white based on the selected point's coordinates.
5. Normalize the original image by dividing it by the maximum pixel values in each channel of the patch.
6. Clip the normalized values between 0 and 1.
7. Display the original image with a rectangle around the selected patch and the white-balanced image.
8. Optionally, you can convert the white-balanced image to 8-bit before saving it.

To use this approach, run the code and follow the instructions in the displayed image. The selected patch will be used to white balance the image, and the white-balanced result will be shown.

## Usage

1. Ensure you have the necessary dependencies installed, particularly OpenCV (`cv2`) and NumPy (`numpy`).
2. Provide the path to the input image by modifying the `img = cv2.imread('lake.png', 1)` line. Replace `'lake.png'` with the path to your desired image.
3. Uncomment the relevant lines to execute either the Gray-world algorithm or the White patch reference method.
4. Run the code and observe the white-balanced image in a separate window.

Feel free to modify the code as needed to suit your requirements.

## Example
1. Input Image:

![Input Image:](https://github.com/BilalSardar009/Image-White-Balancing/blob/main/White%20Balancing/lake.png)

2. Output Image:

![Output Image](https://github.com/BilalSardar009/Image-White-Balancing/blob/main/White%20Balancing/color-balanced.png)
