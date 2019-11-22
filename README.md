# EIP4

Convolution: Convolution is an information aggregation process by reducing noise. This is accomplished by applying a filter over an input.

Filter/Kernel: An operator (a matrix of inputs) applied over an input to generate features (patterns)

Epochs: If an entire dataset is passed once through a neural network it is called as an epoch

1x1 Convolution: A 1x1 matrix ( 1 number) is convoluted over an max pooled image in order to reduce the Z dimension.

3x3 Convolution: A 3x3 matrix of kernel that is convoluted over an image is called as 3x3 convolution.

Feature Maps: The output obtained after applying a kernel/filter over an input is feature maps. In general, the features extracted through one or more layers of convolution

Activation Function: An activation function determines whether the input (summation of weighted sum of inputs and bias) from a node to be fired or not.

Receptive Field: It is defined as the region in the input space that a particular CNN’s feature is looking at after one or more layers of convolution.

Assignment 1 Score: [0.10314206821306968, 0.9924]


## Assignment-2
Logs for 20 Epocs
Train on 60000 samples, validate on 10000 samples
Epoch 1/20
60000/60000 [==============================] - 27s 448us/step - loss: 0.5825 - acc: 0.8387 - val_loss: 0.1488 - val_acc: 0.9817
Epoch 2/20
60000/60000 [==============================] - 21s 353us/step - loss: 0.3386 - acc: 0.8884 - val_loss: 0.0774 - val_acc: 0.9897
Epoch 3/20
60000/60000 [==============================] - 21s 350us/step - loss: 0.2794 - acc: 0.9052 - val_loss: 0.0598 - val_acc: 0.9877
Epoch 4/20
60000/60000 [==============================] - 21s 342us/step - loss: 0.2432 - acc: 0.9169 - val_loss: 0.0511 - val_acc: 0.9893
Epoch 5/20
60000/60000 [==============================] - 21s 348us/step - loss: 0.2165 - acc: 0.9243 - val_loss: 0.0487 - val_acc: 0.9891
Epoch 6/20
60000/60000 [==============================] - 21s 347us/step - loss: 0.1956 - acc: 0.9314 - val_loss: 0.0367 - val_acc: 0.9911
Epoch 7/20
60000/60000 [==============================] - 20s 341us/step - loss: 0.1878 - acc: 0.9330 - val_loss: 0.0336 - val_acc: 0.9905
Epoch 8/20
60000/60000 [==============================] - 21s 342us/step - loss: 0.1755 - acc: 0.9362 - val_loss: 0.0339 - val_acc: 0.9917
Epoch 9/20
60000/60000 [==============================] - 20s 338us/step - loss: 0.1703 - acc: 0.9374 - val_loss: 0.0297 - val_acc: 0.9922
Epoch 10/20
60000/60000 [==============================] - 20s 339us/step - loss: 0.1609 - acc: 0.9411 - val_loss: 0.0329 - val_acc: 0.9914
Epoch 11/20
60000/60000 [==============================] - 20s 338us/step - loss: 0.1567 - acc: 0.9392 - val_loss: 0.0305 - val_acc: 0.9906
Epoch 12/20
60000/60000 [==============================] - 20s 335us/step - loss: 0.1544 - acc: 0.9421 - val_loss: 0.0279 - val_acc: 0.9922
Epoch 13/20
60000/60000 [==============================] - 20s 334us/step - loss: 0.1484 - acc: 0.9425 - val_loss: 0.0271 - val_acc: 0.9915
Epoch 14/20
60000/60000 [==============================] - 21s 343us/step - loss: 0.1439 - acc: 0.9439 - val_loss: 0.0270 - val_acc: 0.9919
Epoch 15/20
60000/60000 [==============================] - 20s 334us/step - loss: 0.1437 - acc: 0.9444 - val_loss: 0.0256 - val_acc: 0.9920
Epoch 16/20
60000/60000 [==============================] - 20s 334us/step - loss: 0.1394 - acc: 0.9456 - val_loss: 0.0301 - val_acc: 0.9915
Epoch 17/20
60000/60000 [==============================] - 20s 340us/step - loss: 0.1368 - acc: 0.9456 - val_loss: 0.0230 - val_acc: 0.9934
Epoch 18/20
60000/60000 [==============================] - 20s 335us/step - loss: 0.1350 - acc: 0.9463 - val_loss: 0.0224 - val_acc: 0.9933
Epoch 19/20
60000/60000 [==============================] - 20s 329us/step - loss: 0.1368 - acc: 0.9458 - val_loss: 0.0239 - val_acc: 0.9930
Epoch 20/20
60000/60000 [==============================] - 20s 331us/step - loss: 0.1307 - acc: 0.9462 - val_loss: 0.0244 - val_acc: 0.9934

<keras.callbacks.History at 0x7f90e07991d0>

### Model Test Score
[0.024351534522185102, 0.9934]

## Startegy
I have made two blocks of convolutin
In each block there are two convolution layers. 2 3X3 conv layers and one 1x1 conv layer followed by max pooling.
 ### Parmeters
 Total params: 15,810
Trainable params: 15,598
Non-trainable params: 212


