

## Things That didn’t work:
•	Polynomial LR
•	Pointwise convolutions to reduce the Z-axis
•	L2 regularization (Weight Decay) (not a significant improvement in generalization at 1e-5)
•	SGD with momentum

## Things That Did work:
•	Rohan’s LR
•	Adam optimizer converged faster
•	Padding in all Conv layers
o	Padding increased layers. More layers better accuracy and better generalization in this case
o	Padding helped in identifying images that are extended till the borders of the image

## Tips and Tricks
•	Overfitting is not a major problem as we must improve the accuracy by only 3-4 percentage points
•	As overfitting is starting after 10 epochs, we can quickly prototype the hyperparameters or different architectures within 20 epochs
•	Any better strategy should yield clear gains in first 10 epochs.
o	In my case  padding, increase in layers and Rohan’s LR improved accuracy within 10 epochs
### Padding is very important as it preserves the output channel size (this helps in adding more layers) and the images are extended till the borders (the input image size is relatively small, 32x32)

Things That Might Work:
•	Data augmentation would have increased validation accuracy

### Final Validation accuracy for Base Network = 0.8233

### Crossed 82.33 (This is the accuracy I need to cross) in the 24th epoch and highest validation score of 83.47 reached in 41st epoch

## Model.Add
model = Sequential()
model.add(SeparableConv2D(filters = 14, kernel_size = 3, padding='same', activation='relu',  input_shape=(32, 32, 3)))
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(SeparableConv2D(filters = 28, kernel_size = 3, padding='same', activation='relu'))#32x32x28 RF = 5
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(SeparableConv2D(filters = 56, kernel_size = 3, padding='same', activation='relu'))#32x32x56 RF = 7
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(SeparableConv2D(filters = 112, kernel_size = 3, padding='same', activation='relu'))#32x32x112 RF = 9
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(SeparableConv2D(filters = 224, kernel_size = 3, padding='same', activation='relu'))#32x32x224 RF = 11
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(MaxPooling2D(pool_size=(2, 2))) #16x16x224 RF = 12

model.add(SeparableConv2D(filters = 28, kernel_size = 3, padding='same', activation='relu'))#16x16x28 RF = 16
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(SeparableConv2D(filters = 56, kernel_size = 3, padding='same', activation='relu' ))#16x16x56 RF = 20
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(SeparableConv2D(filters = 112, kernel_size = 3, padding='same', activation='relu'))#16x16x112 RF = 24
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(SeparableConv2D(filters = 224, kernel_size = 3, padding='same', activation='relu'))#16x16x224 RF = 32
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(MaxPooling2D(pool_size=(2, 2))) #8x8x224 RF = 30

model.add(SeparableConv2D(filters = 28, kernel_size = 3, activation='relu'))#6x6xx28 RF = 38
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(SeparableConv2D(filters = 56, kernel_size = 3, activation='relu'))#4x4x56 RF = 46
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(SeparableConv2D(filters = 112, kernel_size = 3, activation='relu'))#2x2x112 RF = 54
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(Convolution2D(10, 1, 1, activation='relu')) #2x2x10 RF = 54
model.add(BatchNormalization())
model.add(Dropout(0.1))
model.add(GlobalAveragePooling2D()) # 10x1
#model.add(Flatten())
model.add(Activation('softmax'))
model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])

## Logs
Epoch 1/50

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
390/390 [==============================] - 84s 216ms/step - loss: 1.5512 - acc: 0.4472 - val_loss: 2.0603 - val_acc: 0.4440
Epoch 2/50

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
390/390 [==============================] - 42s 108ms/step - loss: 1.0991 - acc: 0.6196 - val_loss: 1.3173 - val_acc: 0.5842
Epoch 3/50

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
390/390 [==============================] - 42s 109ms/step - loss: 0.9256 - acc: 0.6833 - val_loss: 0.8776 - val_acc: 0.7037
Epoch 4/50

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
390/390 [==============================] - 42s 109ms/step - loss: 0.8245 - acc: 0.7189 - val_loss: 0.8495 - val_acc: 0.7213
Epoch 5/50

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
390/390 [==============================] - 44s 114ms/step - loss: 0.7551 - acc: 0.7425 - val_loss: 0.7687 - val_acc: 0.7406
Epoch 6/50

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
390/390 [==============================] - 46s 117ms/step - loss: 0.7025 - acc: 0.7623 - val_loss: 0.7732 - val_acc: 0.7458
Epoch 7/50

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
390/390 [==============================] - 46s 117ms/step - loss: 0.6666 - acc: 0.7763 - val_loss: 0.6551 - val_acc: 0.7847
Epoch 8/50

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
390/390 [==============================] - 44s 113ms/step - loss: 0.6287 - acc: 0.7885 - val_loss: 0.6253 - val_acc: 0.7916
Epoch 9/50

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
390/390 [==============================] - 44s 113ms/step - loss: 0.5921 - acc: 0.8018 - val_loss: 0.6898 - val_acc: 0.7727
Epoch 10/50

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
390/390 [==============================] - 43s 110ms/step - loss: 0.5769 - acc: 0.8060 - val_loss: 0.6328 - val_acc: 0.7906
Epoch 11/50

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
390/390 [==============================] - 43s 110ms/step - loss: 0.5564 - acc: 0.8132 - val_loss: 0.6671 - val_acc: 0.7807
Epoch 12/50

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
390/390 [==============================] - 44s 113ms/step - loss: 0.5364 - acc: 0.8191 - val_loss: 0.6381 - val_acc: 0.7876
Epoch 13/50

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
390/390 [==============================] - 45s 115ms/step - loss: 0.5159 - acc: 0.8275 - val_loss: 0.5771 - val_acc: 0.8072
Epoch 14/50

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
390/390 [==============================] - 44s 112ms/step - loss: 0.4990 - acc: 0.8312 - val_loss: 0.6122 - val_acc: 0.7980
Epoch 15/50

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
390/390 [==============================] - 45s 116ms/step - loss: 0.4930 - acc: 0.8351 - val_loss: 0.5920 - val_acc: 0.8049
Epoch 16/50

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
390/390 [==============================] - 45s 116ms/step - loss: 0.4773 - acc: 0.8409 - val_loss: 0.5740 - val_acc: 0.8112
Epoch 17/50

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
390/390 [==============================] - 45s 116ms/step - loss: 0.4643 - acc: 0.8444 - val_loss: 0.6022 - val_acc: 0.8038
Epoch 18/50

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
390/390 [==============================] - 46s 118ms/step - loss: 0.4533 - acc: 0.8489 - val_loss: 0.5642 - val_acc: 0.8138
Epoch 19/50

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
390/390 [==============================] - 46s 119ms/step - loss: 0.4459 - acc: 0.8518 - val_loss: 0.6056 - val_acc: 0.8012
Epoch 20/50

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
390/390 [==============================] - 47s 119ms/step - loss: 0.4298 - acc: 0.8558 - val_loss: 0.5495 - val_acc: 0.8199
Epoch 21/50

Epoch 00021: LearningRateScheduler setting learning rate to 0.0004065041.
390/390 [==============================] - 46s 117ms/step - loss: 0.4236 - acc: 0.8591 - val_loss: 0.5666 - val_acc: 0.8161
Epoch 22/50

Epoch 00022: LearningRateScheduler setting learning rate to 0.000389661.
390/390 [==============================] - 46s 117ms/step - loss: 0.4180 - acc: 0.8592 - val_loss: 0.5608 - val_acc: 0.8192
Epoch 23/50

Epoch 00023: LearningRateScheduler setting learning rate to 0.0003741581.
390/390 [==============================] - 45s 116ms/step - loss: 0.4137 - acc: 0.8620 - val_loss: 0.5567 - val_acc: 0.8190
Epoch 24/50

Epoch 00024: LearningRateScheduler setting learning rate to 0.0003598417.
390/390 [==============================] - 46s 117ms/step - loss: 0.4031 - acc: 0.8649 - val_loss: 0.5453 - val_acc: 0.8236
Epoch 25/50

Epoch 00025: LearningRateScheduler setting learning rate to 0.0003465804.
390/390 [==============================] - 44s 113ms/step - loss: 0.3967 - acc: 0.8670 - val_loss: 0.5661 - val_acc: 0.8179
Epoch 26/50

Epoch 00026: LearningRateScheduler setting learning rate to 0.0003342618.
390/390 [==============================] - 43s 110ms/step - loss: 0.3916 - acc: 0.8702 - val_loss: 0.5633 - val_acc: 0.8182
Epoch 27/50

Epoch 00027: LearningRateScheduler setting learning rate to 0.0003227889.
390/390 [==============================] - 43s 110ms/step - loss: 0.3847 - acc: 0.8712 - val_loss: 0.5667 - val_acc: 0.8185
Epoch 28/50

Epoch 00028: LearningRateScheduler setting learning rate to 0.0003120774.
390/390 [==============================] - 43s 111ms/step - loss: 0.3768 - acc: 0.8737 - val_loss: 0.5528 - val_acc: 0.8247
Epoch 29/50

Epoch 00029: LearningRateScheduler setting learning rate to 0.000302054.
390/390 [==============================] - 44s 113ms/step - loss: 0.3762 - acc: 0.8740 - val_loss: 0.5698 - val_acc: 0.8182
Epoch 30/50

Epoch 00030: LearningRateScheduler setting learning rate to 0.0002926544.
390/390 [==============================] - 44s 113ms/step - loss: 0.3697 - acc: 0.8767 - val_loss: 0.5481 - val_acc: 0.8247
Epoch 31/50

Epoch 00031: LearningRateScheduler setting learning rate to 0.0002838221.
390/390 [==============================] - 44s 113ms/step - loss: 0.3633 - acc: 0.8805 - val_loss: 0.5450 - val_acc: 0.8258
Epoch 32/50

Epoch 00032: LearningRateScheduler setting learning rate to 0.0002755074.
390/390 [==============================] - 44s 112ms/step - loss: 0.3602 - acc: 0.8800 - val_loss: 0.5577 - val_acc: 0.8239
Epoch 33/50

Epoch 00033: LearningRateScheduler setting learning rate to 0.000267666.
390/390 [==============================] - 44s 112ms/step - loss: 0.3568 - acc: 0.8808 - val_loss: 0.5557 - val_acc: 0.8242
Epoch 34/50

Epoch 00034: LearningRateScheduler setting learning rate to 0.0002602585.
390/390 [==============================] - 44s 112ms/step - loss: 0.3556 - acc: 0.8823 - val_loss: 0.5765 - val_acc: 0.8198
Epoch 35/50

Epoch 00035: LearningRateScheduler setting learning rate to 0.00025325.
390/390 [==============================] - 44s 112ms/step - loss: 0.3483 - acc: 0.8836 - val_loss: 0.5627 - val_acc: 0.8232
Epoch 36/50

Epoch 00036: LearningRateScheduler setting learning rate to 0.0002466091.
390/390 [==============================] - 44s 113ms/step - loss: 0.3446 - acc: 0.8862 - val_loss: 0.5427 - val_acc: 0.8326
Epoch 37/50

Epoch 00037: LearningRateScheduler setting learning rate to 0.0002403076.
390/390 [==============================] - 43s 111ms/step - loss: 0.3413 - acc: 0.8879 - val_loss: 0.5717 - val_acc: 0.8225
Epoch 38/50

Epoch 00038: LearningRateScheduler setting learning rate to 0.0002343201.
390/390 [==============================] - 43s 109ms/step - loss: 0.3411 - acc: 0.8868 - val_loss: 0.6002 - val_acc: 0.8145
Epoch 39/50

Epoch 00039: LearningRateScheduler setting learning rate to 0.0002286237.
390/390 [==============================] - 42s 109ms/step - loss: 0.3334 - acc: 0.8892 - val_loss: 0.5678 - val_acc: 0.8241
Epoch 40/50

Epoch 00040: LearningRateScheduler setting learning rate to 0.0002231977.
390/390 [==============================] - 43s 110ms/step - loss: 0.3302 - acc: 0.8904 - val_loss: 0.5524 - val_acc: 0.8297
Epoch 41/50

Epoch 00041: LearningRateScheduler setting learning rate to 0.0002180233.
390/390 [==============================] - 45s 115ms/step - loss: 0.3316 - acc: 0.8895 - val_loss: 0.5484 - val_acc: 0.8347
Epoch 42/50

Epoch 00042: LearningRateScheduler setting learning rate to 0.0002130833.
390/390 [==============================] - 46s 118ms/step - loss: 0.3260 - acc: 0.8913 - val_loss: 0.5542 - val_acc: 0.8326
Epoch 43/50

Epoch 00043: LearningRateScheduler setting learning rate to 0.0002083623.
390/390 [==============================] - 45s 116ms/step - loss: 0.3229 - acc: 0.8924 - val_loss: 0.5580 - val_acc: 0.8310
Epoch 44/50

Epoch 00044: LearningRateScheduler setting learning rate to 0.0002038459.
390/390 [==============================] - 45s 116ms/step - loss: 0.3214 - acc: 0.8942 - val_loss: 0.5634 - val_acc: 0.8304
Epoch 45/50

Epoch 00045: LearningRateScheduler setting learning rate to 0.0001995211.
390/390 [==============================] - 45s 116ms/step - loss: 0.3206 - acc: 0.8941 - val_loss: 0.5551 - val_acc: 0.8307
Epoch 46/50

Epoch 00046: LearningRateScheduler setting learning rate to 0.0001953761.
390/390 [==============================] - 45s 116ms/step - loss: 0.3127 - acc: 0.8960 - val_loss: 0.5598 - val_acc: 0.8306
Epoch 47/50

Epoch 00047: LearningRateScheduler setting learning rate to 0.0001913998.
390/390 [==============================] - 47s 119ms/step - loss: 0.3124 - acc: 0.8954 - val_loss: 0.5605 - val_acc: 0.8305
Epoch 48/50

Epoch 00048: LearningRateScheduler setting learning rate to 0.0001875821.
390/390 [==============================] - 45s 116ms/step - loss: 0.3110 - acc: 0.8961 - val_loss: 0.5929 - val_acc: 0.8233
Epoch 49/50

Epoch 00049: LearningRateScheduler setting learning rate to 0.0001839137.
390/390 [==============================] - 45s 116ms/step - loss: 0.3050 - acc: 0.8998 - val_loss: 0.5761 - val_acc: 0.8249
Epoch 50/50

Epoch 00050: LearningRateScheduler setting learning rate to 0.000180386.
390/390 [==============================] - 43s 111ms/step - loss: 0.3058 - acc: 0.8981 - val_loss: 0.5674 - val_acc: 0.8312
Model took 2279.78 seconds to train
