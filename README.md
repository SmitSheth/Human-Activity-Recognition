# Human-Activity-Recognition
This experiment is classification of human activties using 2D pose time series dataset and an LSTM. The idea is to use pose estimations obtained using OpenPose and classify the human actions. The current project can detect action only when single person is persent in the video.

# Dataset Overview
The dataset consists of pose estimations, made using the  OpenPose (OpenCV version) on a subset of the Berkeley Multimodal Human Action Database (MHAD) dataset http://tele-immersion.citris-uc.org/berkeley_mhad.

This dataset is comprised of 12 subjects doing the following 6 actions for 5 repetitions, filmed from 4 angles, repeated 5 times each.

*JUMPING,
*JUMPING_JACKS,
*BOXING,
*WAVING_2HANDS,
*WAVING_1HAND,
*CLAPPING_HANDS.

The input for the model is the 2D position of 18 joints across a timeseries of frames numbering n_steps (window-width), with an associated class label for each frame series.
A single frame's input (where j refers to a joint) is stored as:

[ j0_x, j0_y, j1_x, j1_y , j2_x, j2_y, j3_x, j3_y, j4_x, j4_y, j5_x, j5_y, j6_x, j6_y, j7_x, j7_y, j8_x, j8_y, j9_x, j9_y, j10_x, j10_y, j11_x, j11_y, j12_x, j12_y, j13_x, j13_y, j14_x, j14_y, j15_x, j15_y, j16_x, j16_y, j17_x, j17_y ]

For the following experiment, very little preprocessing has been done to the dataset.
The following steps were taken:

*openpose run on individual frames, for each subject, action and view, outputting 18 joints x and y position keypoints and accuracies per frame
*Output converted into csv format, keeping only x and y positions of each frame, action being performed during frame, and order of frames. This is used to create a database of associated activity class number and corresponding series of joint 2D positions.
Note:- In cases where  multiple people were detected in each frame, only the first detection was used. 

# References
The dataset can be found at http://tele-immersion.citris-uc.org/berkeley_mhad released under the BSD-2 license
>Copyright (c) 2013, Regents of the University of California All rights reserved.

The model reference is taken from :
>https://github.com/guillaume-chevalier/LSTM-Human-Activity-Recognition
