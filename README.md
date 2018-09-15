# Self-Driving-Car-SteeringDirectionPrediction

## Packages needed

```console
terminal@linux:~$ conda create env --file environments.yml
terminal@linux:~$ source activate car-simulation
```
<hr>

## Training 
<p>Run the self driving car simulator in training mode , which will collect all the datas from 3 virtual cameras in the car and direction of sttering which you turn as the dependent variable. Use this CSV file to train the model woth a convolution neural network.</p>

```console
terminal@linux:~$ python model.py 
```
<p> You may need a GPU for this training , it took forever for me to train</p>

<hr>

---
### Model

The model is obtained from the **[Nvidia paper](end-to-end-dl-using-px.pdf)**, built with *Keras*, and have total **154,132 parameters**. The summary of the model is shown as below:

| Layer (type) | Output Shape | Param # | Connected to |
| :--- | :--- | ---: | :--- |
| lambda_1 (Lambda) | (None, 66, 200, 3) | 0 | lambda_input_1[0][0] |
| convolution2d_1 (Convolution2D) | (None, 33, 100, 5) | 1805 | lambda_1[0][0] |
| maxpooling2d_1 (MaxPooling2D) | (None, 16, 50, 5) | 1805 | convolution2d_1[0][0] |
| elu_1 (ELU) | (None, 16, 50, 5) | 0 | convolution2d_1[0][0] |
| convolution2d_2 (Convolution2D) |(None, 8, 25, 5) | 4505 | elu_1[0][0] |
| elu_2 (ELU) |(None, 8, 25, 5) | 0 | convolution2d_2[0][0] |
| convolution2d_3 (Convolution2D) |(None, 4, 13, 5) | 6005 | elu_2[0][0] |
| elu_3 (ELU) |(None, 4, 13, 5) | 0 | convolution2d_3[0][0] |
| convolution2d_4 (Convolution2D) |(None, 2, 7, 3) | 2883 | elu_3[0][0] |
| elu_4 (ELU) |(None, 2, 7, 3) | 0 | convolution2d_4[0][0] |
| convolution2d_5 (Convolution2D) |(None, 1, 4, 3) | 1731 | elu_4[0][0] |
| flatten_1 (Flatten) | (None, 12) | 0 | convolution2d_5[0][0] |
| dropout_1 (Dropout) | (None, 12) | 0 | flatten_1[0][0] |
| elu_5 (ELU) | (None, 12) | 0 | dropout_1[0][0] |
| dense_1 (Dense) | (None, 1164) | 8148 | elu_5[0][0] |
| dropout_2 (Dropout) | (None, 1164) | 0 | dense_1[0][0] |
| elu_6 (ELU) | (None, 1164) | 0 | dropout_2[0][0] |
| dense_2 (Dense) | (None, 100) | 116500 | elu_6[0][0] |
| dropout_3 (Dropout) | (None, 100) | 0 | dense_2[0][0] |
| elu_7 (ELU) | (None, 100) | 0 | dropout_3[0][0] |
| dense_3 (Dense) | (None, 50) | 5050 | elu_7[0][0] |
| dropout_4 (Dropout) | (None, 50) | 0 | dense_3[0][0] |
| elu_8 (ELU) | (None, 50) | 0 | dropout_4[0][0] |
| dense_4 (Dense) | (None, 10) | 510 | elu_8[0][0] |
| dropout_5 (Dropout) | (None, 10) | 0 | dense_4[0][0] |
| elu_9 (ELU) | (None, 10) | 0 | dropout_5[0][0] |
| dense_5 (Dense) | (None, 1) | 11 | elu_9[0][0] |

---


## Tesing the model with the self driving car
<p>Use the flask server to send the steering directions for any given time for the inputs from 3 virtual cameras in the car.</p>

```console
terminal@linux:~$ python drive.py model.h5
```

<hr>

## Demo
[[Demo]](https://youtu.be/-KjL1NJcgUs)


## Run the Code

```console
terminal@linux:~$ python detect_lanes_video.py
```






## Screenshot
### Autonomous mode 
![Output](img.png)

