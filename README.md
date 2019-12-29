# EIP4- Assignment_1


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



## Startegy-1
I have made two blocks of convolutins
In each block there are two convolution layers. 2 3X3 conv layers and one 1x1 conv layer followed by max pooling.
But I didn't incorporate learning rate scheduler.
May be if I implemnt that I may get 99.4 test accuracy.


 ### Parmeters
 Total params: 15,810
Trainable params: 15,598
Non-trainable params: 212

### Model Test Score
[0.024351534522185102, 0.9934]



## Startegy-2
This time I scheduled learning rate and was able to aacheive 99.38 test accuracy. Validation accuracy reached 0.994 at least six times in the 20 epochs.

Logs of 20 Epocs after scheduling learning rate
Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
60000/60000 [==============================] - 14s 226us/step - loss: 0.0966 - acc: 0.9555 - val_loss: 0.0261 - val_acc: 0.9922
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
60000/60000 [==============================] - 6s 101us/step - loss: 0.0923 - acc: 0.9562 - val_loss: 0.0244 - val_acc: 0.9920
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
60000/60000 [==============================] - 6s 100us/step - loss: 0.0869 - acc: 0.9582 - val_loss: 0.0196 - val_acc: 0.9935
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0848 - acc: 0.9579 - val_loss: 0.0205 - val_acc: 0.9932
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0857 - acc: 0.9579 - val_loss: 0.0184 - val_acc: 0.9940
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
60000/60000 [==============================] - 6s 100us/step - loss: 0.0808 - acc: 0.9589 - val_loss: 0.0214 - val_acc: 0.9935
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
60000/60000 [==============================] - 6s 101us/step - loss: 0.0816 - acc: 0.9583 - val_loss: 0.0182 - val_acc: 0.9943
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
60000/60000 [==============================] - 6s 100us/step - loss: 0.0795 - acc: 0.9594 - val_loss: 0.0206 - val_acc: 0.9938
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0801 - acc: 0.9598 - val_loss: 0.0189 - val_acc: 0.9937
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
60000/60000 [==============================] - 6s 97us/step - loss: 0.0785 - acc: 0.9600 - val_loss: 0.0211 - val_acc: 0.9925
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0801 - acc: 0.9592 - val_loss: 0.0190 - val_acc: 0.9940
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0783 - acc: 0.9589 - val_loss: 0.0197 - val_acc: 0.9935
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
60000/60000 [==============================] - 6s 99us/step - loss: 0.0765 - acc: 0.9600 - val_loss: 0.0197 - val_acc: 0.9932
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0759 - acc: 0.9610 - val_loss: 0.0215 - val_acc: 0.9931
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
60000/60000 [==============================] - 6s 97us/step - loss: 0.0749 - acc: 0.9618 - val_loss: 0.0209 - val_acc: 0.9933
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
60000/60000 [==============================] - 6s 100us/step - loss: 0.0762 - acc: 0.9604 - val_loss: 0.0182 - val_acc: 0.9940
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
60000/60000 [==============================] - 6s 99us/step - loss: 0.0752 - acc: 0.9598 - val_loss: 0.0184 - val_acc: 0.9941
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0766 - acc: 0.9603 - val_loss: 0.0183 - val_acc: 0.9940
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0742 - acc: 0.9613 - val_loss: 0.0177 - val_acc: 0.9942
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
60000/60000 [==============================] - 6s 98us/step - loss: 0.0753 - acc: 0.9601 - val_loss: 0.0181 - val_acc: 0.9938

<keras.callbacks.History at 0x7f90e039e0b8>

### Test accuracy
score = model.evaluate(X_test, Y_test, verbose=0)
print(score)
[0.018072435555551783, 0.9938]


## Startegy-3
I know the above architecture slightly exceeded 15000 parameters. This time I have slightly changed the architecture by reducing the last point convolution layer channels to 10 instead of 16 (10 beacuse I have 10 classes.). This architecture along with the learning rate scheduler, 99.4 test accuracy was acheived within 15000 parameters and 20 epochs.

### Epochs
Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
60000/60000 [==============================] - 12s 207us/step - loss: 0.4338 - acc: 0.8747 - val_loss: 0.0921 - val_acc: 0.9828
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
60000/60000 [==============================] - 9s 158us/step - loss: 0.2263 - acc: 0.9257 - val_loss: 0.0573 - val_acc: 0.9878
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
60000/60000 [==============================] - 10s 159us/step - loss: 0.1841 - acc: 0.9384 - val_loss: 0.0466 - val_acc: 0.9900
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
60000/60000 [==============================] - 9s 156us/step - loss: 0.1590 - acc: 0.9431 - val_loss: 0.0397 - val_acc: 0.9911
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
60000/60000 [==============================] - 9s 156us/step - loss: 0.1449 - acc: 0.9471 - val_loss: 0.0439 - val_acc: 0.9878
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
60000/60000 [==============================] - 9s 156us/step - loss: 0.1370 - acc: 0.9472 - val_loss: 0.0371 - val_acc: 0.9908
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
60000/60000 [==============================] - 9s 155us/step - loss: 0.1299 - acc: 0.9490 - val_loss: 0.0290 - val_acc: 0.9919
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
60000/60000 [==============================] - 9s 155us/step - loss: 0.1252 - acc: 0.9497 - val_loss: 0.0318 - val_acc: 0.9906
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
60000/60000 [==============================] - 9s 156us/step - loss: 0.1228 - acc: 0.9498 - val_loss: 0.0294 - val_acc: 0.9920
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
60000/60000 [==============================] - 9s 155us/step - loss: 0.1184 - acc: 0.9512 - val_loss: 0.0314 - val_acc: 0.9908
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
60000/60000 [==============================] - 9s 154us/step - loss: 0.1109 - acc: 0.9536 - val_loss: 0.0243 - val_acc: 0.9933
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
60000/60000 [==============================] - 9s 157us/step - loss: 0.1124 - acc: 0.9524 - val_loss: 0.0243 - val_acc: 0.9927
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
60000/60000 [==============================] - 10s 162us/step - loss: 0.1119 - acc: 0.9524 - val_loss: 0.0234 - val_acc: 0.9930
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
60000/60000 [==============================] - 9s 155us/step - loss: 0.1060 - acc: 0.9542 - val_loss: 0.0232 - val_acc: 0.9937
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
60000/60000 [==============================] - 9s 156us/step - loss: 0.1072 - acc: 0.9537 - val_loss: 0.0236 - val_acc: 0.9935
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
60000/60000 [==============================] - 9s 155us/step - loss: 0.1056 - acc: 0.9539 - val_loss: 0.0213 - val_acc: 0.9941
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
60000/60000 [==============================] - 9s 152us/step - loss: 0.1073 - acc: 0.9530 - val_loss: 0.0227 - val_acc: 0.9934
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
60000/60000 [==============================] - 9s 154us/step - loss: 0.1020 - acc: 0.9549 - val_loss: 0.0212 - val_acc: 0.9939
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
60000/60000 [==============================] - 9s 154us/step - loss: 0.1009 - acc: 0.9559 - val_loss: 0.0205 - val_acc: 0.9942
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
60000/60000 [==============================] - 9s 154us/step - loss: 0.1008 - acc: 0.9558 - val_loss: 0.0216 - val_acc: 0.9941

### Architecture
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d_20 (Conv2D)           (None, 26, 26, 16)        160       
_________________________________________________________________
batch_normalization_14 (Batc (None, 26, 26, 16)        64        
_________________________________________________________________
dropout_14 (Dropout)         (None, 26, 26, 16)        0         
_________________________________________________________________
conv2d_21 (Conv2D)           (None, 24, 24, 32)        4640      
_________________________________________________________________
batch_normalization_15 (Batc (None, 24, 24, 32)        128       
_________________________________________________________________
dropout_15 (Dropout)         (None, 24, 24, 32)        0         
_________________________________________________________________
conv2d_22 (Conv2D)           (None, 24, 24, 16)        528       
_________________________________________________________________
max_pooling2d_7 (MaxPooling2 (None, 12, 12, 16)        0         
_________________________________________________________________
conv2d_23 (Conv2D)           (None, 10, 10, 16)        2320      
_________________________________________________________________
batch_normalization_16 (Batc (None, 10, 10, 16)        64        
_________________________________________________________________
dropout_16 (Dropout)         (None, 10, 10, 16)        0         
_________________________________________________________________
conv2d_24 (Conv2D)           (None, 8, 8, 32)          4640      
_________________________________________________________________
batch_normalization_17 (Batc (None, 8, 8, 32)          128       
_________________________________________________________________
dropout_17 (Dropout)         (None, 8, 8, 32)          0         
_________________________________________________________________
max_pooling2d_8 (MaxPooling2 (None, 4, 4, 32)          0         
_________________________________________________________________
conv2d_25 (Conv2D)           (None, 4, 4, 10)          330       
_________________________________________________________________
conv2d_26 (Conv2D)           (None, 1, 1, 10)          1610      
_________________________________________________________________
batch_normalization_18 (Batc (None, 1, 1, 10)          40        
_________________________________________________________________
dropout_18 (Dropout)         (None, 1, 1, 10)          0         
_________________________________________________________________
flatten_4 (Flatten)          (None, 10)                0         
_________________________________________________________________
activation_4 (Activation)    (None, 10)                0         
=================================================================
Total params: 14,652
Trainable params: 14,440
Non-trainable params: 212

### Test Accuracy
[0.021593860066635533, 0.9941]

Notebook 1: https://github.com/bharathbolla/EIP4/blob/master/Assignment_2.ipynb
Notebook 2: https://github.com/bharathbolla/EIP4/blob/master/Assignment_2_with%20LR_Schedule.ipynb
Notebook 3: https://github.com/bharathbolla/EIP4/blob/master/EIP4_Assignment2_Ver3.0.ipynb
