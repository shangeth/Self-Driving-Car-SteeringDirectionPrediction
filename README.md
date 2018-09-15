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

