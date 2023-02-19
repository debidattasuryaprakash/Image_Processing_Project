# Image Processing

Image processing in C++ involves manipulating the pixel values of an image to achieve a desired effect. This is typically done by applying various mathematical formulas and operations to the pixel values.

- **Grayscale Conversion**: This operation converts a color image to grayscale by taking the average value of the red, green, and blue color channels for each pixel.

```cpp
void grayscale(cv::Mat& image) {
    cv::cvtColor(image, image, cv::COLOR_BGR2GRAY);
}
```

- **Sepia Tone**: This operation gives an image a warm, brownish tone by manipulating the RGB values of each pixel according to a specific formula.

```cpp
void sepia(cv::Mat& image) {
    for (int i = 0; i < image.rows; i++) {
        for (int j = 0; j < image.cols; j++) {
            cv::Vec3b color = image.at<cv::Vec3b>(i, j);
            int r = color[2];
            int g = color[1];
            int b = color[0];

            int tr = std::min(255, (int)(0.393 * r + 0.769 * g + 0.189 * b));
            int tg = std::min(255, (int)(0.349 * r + 0.686 * g + 0.168 * b));
            int tb = std::min(255, (int)(0.272 * r + 0.534 * g + 0.131 * b));

            image.at<cv::Vec3b>(i, j) = cv::Vec3b(tb, tg, tr);
        }
    }
}
```

- **Gaussian Blur**: This operation blurs an image to reduce noise and smooth out imperfections. It applies a Gaussian filter to each pixel, which is calculated using a specific formula.

```cpp
void gaussianBlur(cv::Mat& image, int kernelSize) {
    cv::GaussianBlur(image, image, cv::Size(kernelSize, kernelSize), 0, 0);
}
```
