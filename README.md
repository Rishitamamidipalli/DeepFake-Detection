# DeepFake Detection
Detecting deepfake videos based on Eye and Mouth features using CNN and LSTM models.

# Table of Contents
-[Introduction](#Introduction)

-[Methodology](#Methodology)

-[Data Preparation](#Data-Preparation)

-[Feature Extraction with ResNext](#Feature-Extraction-with-ResNext)

-[Results](#Results)
* * *
# Introduction
This projects aims in detection of video deepfakes using deep learning techniques like ResNext and LSTM. We have achived deepfake detection by using transfer learning where the pretrained ResNext CNN is used to obtain a feature vector, further the LSTM layer is trained using the features
* * *
### Methodology
![Screenshot 2024-07-02 122506](https://github.com/Rishitamamidipalli/DeepFake-Detection/assets/123208162/1f61cf1f-b3fe-49a1-af3a-3b80404adbc0)
* * *
### Data Preparation
Initially, videos are sourced from the Celeb-DF dataset. These videos are labeled based on their file paths for clarity and organization. From each video, 30 frames are extracted to facilitate detailed analysis. The detection and cropping of eye and mouth regions from each frame are performed using a pre-trained model from dlib (shape_predictor_68_face_landmarks.dat). The eyes and mouth regions are identified using the extreme left and right landmarks. These cropped regions are then resized to 100x50 pixels. Subsequently, the eye and mouth images are merged vertically, resulting in a final image resolution of 112x112 pixels.

![Screenshot 2024-07-02 122706](https://github.com/Rishitamamidipalli/DeepFake-Detection/assets/123208162/30c4838d-63fb-486f-bc00-a4a5e238b298)
* * *
### Feature Extraction with ResNext
For feature extraction, we employ a pre-trained ResNext model (specifically the resnext50 32x4d variant). This model is known for its proficiency in deep neural networks, consisting of 50 layers with 32 nodes each, forming a four-dimensional architecture with approximately 25 million learnable parameters. From this model, we obtain a 2048-dimensional feature vector derived from the last pooling layers, which serves as the input for the LSTM layer.

![Screenshot 2024-07-02 122752](https://github.com/Rishitamamidipalli/DeepFake-Detection/assets/123208162/20446dcd-4d6e-4429-9496-bc3b01e0e355)

Sequence Processing with LSTM
Following feature extraction, the 2048-dimensional feature vectors are input into a single LSTM layer for sequence processing. The LSTM layer is configured with 2048 latent dimensions, augmented with a dropout probability of 0.4 to mitigate overfitting. This LSTM architecture is pivotal in analyzing the temporal dynamics and dependencies within the video sequences. By leveraging the LSTM’s ability to model sequential data, our model effectively captures the nuanced patterns indicative of deepfake or real videos.
* * *
### Results

The Celeb-DF dataset of 1800 videos(fake-900 , real-900) was split into train and test sets with 80-20 ratio.

![Screenshot 2024-07-02 133502](https://github.com/Rishitamamidipalli/DeepFake-Detection/assets/123208162/a184ebcc-ac15-4763-b9da-0acc8a25b25e)
