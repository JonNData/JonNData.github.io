---
layout: post
title: Speech Emotion 
subtitle: Analyze audio clips to determine their emotion
image: https://miro.medium.com/max/1620/0*tqQ-x7QM2zKhJB9F.jpg
tags: [Neural Network, Audio Analysis, Fast Api, python]
---

# Speech Emotion Detector
View the video rundown [here](https://www.linkedin.com/posts/jonathan-nguyen-94344b21_python-neuralnetwork-activity-6747693412549558272-Ow-Y)

Detect emotion in an audio clip

Trained on Ryerson Audio-Visual Database of Emotional Speech and Song dataset.
Audio clips from the RADVESS dataset are classified as: 
```
emotions={
  '01':'neutral',
  '02':'calm',
  '03':'happy',
  '04':'sad',
  '05':'angry',
  '06':'fearful',
  '07':'disgust',
  '08':'surprised'
}
```
We will use Machine Learning to classify a subsection of them as either:
`('calm', 'happy', 'fearful', 'disgust')`

First we use librosa library for analyzing and extracting audio features.
Next, we read in the data and train a model.
After we evaluate the model we can use it for predicting the emotion of other audio clips.

Note: file_name[6] refers to the gender of the speaker. Might it be a stretch to also predict the gender of a speaker?

We can read in WAV files, preferrably in mono but conversion is handled as well.

Steps: 
Ask for the upload, check file extension, save audio file, run predicitons and graphs, save graphs, display graphs and predictions.
