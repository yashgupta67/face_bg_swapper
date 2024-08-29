# Face and Background Swapper App

This project is a face and background swapping application that uses deep learning models to detect faces in images, swap them with another face, and change the background while preserving the subject(s) in the image.

## Features

- **Face Swapping**: Swap faces in an image with a given source image while maintaining the target image's body and other features.
- **Background Replacement**: Replace the background of the target image while keeping the subject(s) intact.
- **Real-time Processing**: Process images in real-time using pre-trained models for face detection and semantic segmentation.

## Getting Started

### Prerequisites

- Python 3.7 or higher
- `pip` (Python package installer)

### Approach

#### Face Swapping using inswapper_128.onnx
The face swapping feature in this application leverages the inswapper_128.onnx model from InsightFace. This model is designed specifically for face swapping tasks and works as follows:

- **Face Detection**: The FaceAnalysis class from the InsightFace library is used to detect faces in both the source and target images. The buffalo_l model is used for this purpose, which is capable of detecting multiple faces in an image with high accuracy.

- **Face Alignment and Swapping**: Once faces are detected, the inswapper_128.onnx model aligns the source face with the detected face in the target image. The model then blends the source face into the target image seamlessly, ensuring that facial features such as expression and orientation are preserved.

- **Final Composition**: The swapped face is combined with the rest of the target image, maintaining the integrity of the body and other features. This process allows for a natural and realistic face swap, suitable for various applications.

#### Background Replacement using rembg
For background replacement, this application uses the rembg library, which is based on a pre-trained U2-Net model. The approach is as follows:

- **Background Removal**: The remove function from the rembg library is employed to segment and remove the background from the target image. This function processes the image and generates a binary mask that differentiates the subject(s) from the background.

- **New Background Application**: After removing the original background, a new background image can be added behind the subject(s). The PIL.Image module is used to handle image compositing, allowing for seamless integration of the subject(s) with the new background.

= **Final Output**: The result is a high-quality image where the subject(s) remain intact while the background has been replaced. This technique is particularly useful for applications like virtual backgrounds, image editing, and creative photo manipulation.
