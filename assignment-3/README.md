# S5

Data Overview


MNIST ("Modified National Institute of Standards and Technology") dataset of computer vision. The MNIST database contains 60,000 training images and 10,000 testing images. Half of the training set and half of the test set were taken from NIST's training dataset, while the other half of the training set and the other half of the test set were taken from NIST's testing dataset.This project implements a beginner classification task on MNIST dataset with a Convolutional Neural Network(CNN) model.

![image](https://user-images.githubusercontent.com/70502759/137764343-c1134fa1-94d2-40b0-bf21-dcd78b3ed4e1.png)
  
  This project will automatically dowload and process the MNIST dataset
  
  Design the model architecture for MNIST with following constraint :
    
    99.4% validation accuracy
    Less than 10k Parameters
    Less than 15 Epochs


Step 1: 
   
       


     1 - Changes done:

        1 - Get the basic setup

        2 - Set Transforms

             Model Summary : 
       
         ----------------------------------------------------------------
         Layer (type)               Output Shape         Param #
         ================================================================
             Conv2d-1           [-1, 10, 26, 26]              90
          BatchNorm2d-2           [-1, 10, 26, 26]            20
              ReLU-3           [-1, 10, 26, 26]               0
            Conv2d-4           [-1, 10, 24, 24]               900
          BatchNorm2d-5           [-1, 10, 24, 24]            20
              ReLU-6           [-1, 10, 24, 24]               0
            Conv2d-7           [-1, 20, 22, 22]               1,800
          BatchNorm2d-8           [-1, 20, 22, 22]            40
              ReLU-9           [-1, 20, 22, 22]               0
          MaxPool2d-10           [-1, 20, 11, 11]             0
           Conv2d-11           [-1, 10, 11, 11]               200
          BatchNorm2d-12           [-1, 10, 11, 11]           20
             ReLU-13           [-1, 10, 11, 11]               0
           Conv2d-14             [-1, 10, 9, 9]               900
          BatchNorm2d-15             [-1, 10, 9, 9]           20
             ReLU-16             [-1, 10, 9, 9]               0
           Conv2d-17             [-1, 20, 7, 7]               1,800
          BatchNorm2d-18             [-1, 20, 7, 7]           40
             ReLU-19             [-1, 20, 7, 7]               0
           Conv2d-20             [-1, 10, 7, 7]               200
          BatchNorm2d-21             [-1, 10, 7, 7]           20
             ReLU-22             [-1, 10, 7, 7]               0
           Conv2d-23             [-1, 10, 1, 1]               4,900
        ================================================================
        Total params: 10,970
        Trainable params: 10,970
        Non-trainable params: 0
        ----------------------------------------------------------------
       Input size (MB): 0.00
       Forward/backward pass size (MB): 0.61
       Params size (MB): 0.04
       Estimated Total Size (MB): 0.65
       ----------------------------------------------------------------

    Target :
    -------
    
     1 - Set Data Loader

     2 - Set Basic Working Code

     3 - Set Basic Training & Test Loop
     
     4 - apply the normalization for input image along with batch normalization

     5 - Results:

         1 - Parameters: 10,970
         2 - Best Training Accuracy: 99.76
         3 - Best Test Accuracy: 99.14

     6 - Inference:

  
         1 - Model is slightly over-fitting as traing accuracy is high and  gap between training and testing accuracy is more ,
             if we increase training accuracy also we will not acive accuracy of 99.4%  
         2 - Also from loss and accuracy diagram its looks like learning rate is bit high as its fluctuating 
             
             
 ![image](https://user-images.githubusercontent.com/70502759/213490135-c4a9c00b-230a-4911-865e-dd2a2270863d.png)


Step 2 : 
    

    1 - Changes done:

         1 - There is overfitting, hence added Regularization with the help of  Dropout , which interns help us in reducing overfitting.
             Also adding gap layer to remove the large kernel layer from last

           Model Summary : 
   
       ----------------------------------------------------------------
            Layer (type)               Output Shape         Param #
    ================================================================
            Conv2d-1           [-1, 15, 26, 26]             135
       BatchNorm2d-2           [-1, 15, 26, 26]              30
              ReLU-3           [-1, 15, 26, 26]               0
            Conv2d-4           [-1, 10, 24, 24]           1,350
       BatchNorm2d-5           [-1, 10, 24, 24]              20
              ReLU-6           [-1, 10, 24, 24]               0
            Conv2d-7           [-1, 25, 22, 22]           2,250
       BatchNorm2d-8           [-1, 25, 22, 22]              50
              ReLU-9           [-1, 25, 22, 22]               0
          Dropout-10           [-1, 25, 22, 22]               0
        MaxPool2d-11           [-1, 25, 11, 11]               0
           Conv2d-12           [-1, 20, 11, 11]             500
      BatchNorm2d-13           [-1, 20, 11, 11]              40
             ReLU-14           [-1, 20, 11, 11]               0
           Conv2d-15             [-1, 15, 9, 9]           2,700
      BatchNorm2d-16             [-1, 15, 9, 9]              30
             ReLU-17             [-1, 15, 9, 9]               0
           Conv2d-18             [-1, 10, 7, 7]           1,350
      BatchNorm2d-19             [-1, 10, 7, 7]              20
             ReLU-20             [-1, 10, 7, 7]               0
          Dropout-21             [-1, 10, 7, 7]               0
           Conv2d-22             [-1, 10, 5, 5]             900
      BatchNorm2d-23             [-1, 10, 5, 5]              20
             ReLU-24             [-1, 10, 5, 5]               0
        AvgPool2d-25             [-1, 10, 1, 1]               0
    ================================================================
    Total params: 9,395
    Trainable params: 9,395
    Non-trainable params: 0
    ----------------------------------------------------------------
    Input size (MB): 0.00
    Forward/backward pass size (MB): 0.86
    Params size (MB): 0.04
    Estimated Total Size (MB): 0.90
    ----------------------------------------------------------------


    2 - Results:

         1 - Parameters: 9,395
         2 - Best Training Accuracy: 99.35
         3 - Best Test Accuracy: 99.30

    3 - Inference:

             1 - We could see batch-norm help us in enhancing the model efficiency 
             2 - We could see dropout helps us in reducing overfitting . 
                 We could see the model perform slightly better on test data .
             3 - If we push this model further there is a high chance we can achieve the target of 99.4
             4 - We are also not using GAP, but depending on a BIG sized kernel at the last layer we will fix this in next step .
    4 - last training logs
         
    EPOCH: 9
    Loss=0.002981663914397359 Batch_id=468 Accuracy=99.23: 100%|██████████| 469/469 [00:13<00:00, 35.50it/s]
    Test set: Average loss: 0.0267, Accuracy: 9924/10000 (99.24%)

    EPOCH: 10
    Loss=0.023660933598876 Batch_id=468 Accuracy=99.21: 100%|██████████| 469/469 [00:13<00:00, 35.07it/s]
    Test set: Average loss: 0.0249, Accuracy: 9928/10000 (99.28%)

    EPOCH: 11
    Loss=0.017755737528204918 Batch_id=468 Accuracy=99.29: 100%|██████████| 469/469 [00:13<00:00, 34.85it/s]
    Test set: Average loss: 0.0253, Accuracy: 9921/10000 (99.21%)

    EPOCH: 12
    Loss=0.009737336076796055 Batch_id=468 Accuracy=99.31: 100%|██████████| 469/469 [00:13<00:00, 34.56it/s]
    Test set: Average loss: 0.0290, Accuracy: 9915/10000 (99.15%)

    EPOCH: 13
    Loss=0.028894586488604546 Batch_id=468 Accuracy=99.35: 100%|██████████| 469/469 [00:14<00:00, 33.02it/s]
    Test set: Average loss: 0.0252, Accuracy: 9930/10000 (99.30%)

    EPOCH: 14
    Loss=0.016243664547801018 Batch_id=468 Accuracy=99.34: 100%|██████████| 469/469 [00:13<00:00, 35.24it/s]
    Test set: Average loss: 0.0279, Accuracy: 9921/10000 (99.21%)
![image](https://user-images.githubusercontent.com/70502759/213735181-69d08b01-e2d8-4afe-a9a9-5f360c11b6bc.png)


Step 3 : 

       ----------------------------------------------------------------
            Layer (type)               Output Shape         Param #
    ================================================================
            Conv2d-1           [-1, 15, 26, 26]             135
       BatchNorm2d-2           [-1, 15, 26, 26]              30
              ReLU-3           [-1, 15, 26, 26]               0
            Conv2d-4           [-1, 10, 24, 24]           1,350
       BatchNorm2d-5           [-1, 10, 24, 24]              20
              ReLU-6           [-1, 10, 24, 24]               0
            Conv2d-7           [-1, 25, 22, 22]           2,250
       BatchNorm2d-8           [-1, 25, 22, 22]              50
              ReLU-9           [-1, 25, 22, 22]               0
          Dropout-10           [-1, 25, 22, 22]               0
        MaxPool2d-11           [-1, 25, 11, 11]               0
           Conv2d-12           [-1, 20, 11, 11]             500
      BatchNorm2d-13           [-1, 20, 11, 11]              40
             ReLU-14           [-1, 20, 11, 11]               0
           Conv2d-15             [-1, 15, 9, 9]           2,700
      BatchNorm2d-16             [-1, 15, 9, 9]              30
             ReLU-17             [-1, 15, 9, 9]               0
           Conv2d-18             [-1, 10, 7, 7]           1,350
      BatchNorm2d-19             [-1, 10, 7, 7]              20
             ReLU-20             [-1, 10, 7, 7]               0
          Dropout-21             [-1, 10, 7, 7]               0
           Conv2d-22             [-1, 10, 5, 5]             900
      BatchNorm2d-23             [-1, 10, 5, 5]              20
             ReLU-24             [-1, 10, 5, 5]               0
        AvgPool2d-25             [-1, 10, 1, 1]               0
    ================================================================
    Total params: 9,395
    Trainable params: 9,395
    Non-trainable params: 0
    ----------------------------------------------------------------
    Input size (MB): 0.00
    Forward/backward pass size (MB): 0.86
    Params size (MB): 0.04
    Estimated Total Size (MB): 0.90
    ----------------------------------------------------------------

     1 - Changes done:

         1 - Added GAP and remove the last gig size kernel And then Increase model capacity by adding more layers at the end.

      Model Summary : 



     2 - Changes done:

         1 - Parameters: 9395

         2 - Best Training Accuracy: 99.34 (At EPOCH -14)

         3 - Best Test Accuracy: 99.34 (At EPOCH -13)

     3 - Inference:

         1 - Adding Global Average Pooling reduces model parameters i.e interns
             reduced model capacity , hence a reduction in performance is expected.
             Then we have decided to further increase the model capacity .
         2 - Value of drop out (.10) did not allow training accuracy beyond 
             98.80 - 99.01. Hence we have decided to keep very low values of 
             dropout(.007) which help us increase the training accuracy .
        3 - The model did not showing over-fitting possibly DropOut can be 
            ignore , rather removing it completely we have decided to keep it 
            with very less dropout percentage
      
      4 - few traing logs
      
          EPOCH: 8
    Loss=0.06473712623119354 Batch_id=468 Accuracy=99.13: 100%|██████████| 469/469 [00:18<00:00, 25.54it/s]
        Test set: Average loss: 0.0210, Accuracy: 9938/10000 (99.38%)

    EPOCH: 9
    Loss=0.020384931936860085 Batch_id=468 Accuracy=99.23: 100%|██████████| 469/469 [00:18<00:00, 24.80it/s]
        Test set: Average loss: 0.0186, Accuracy: 9940/10000 (99.40%)

    EPOCH: 10
    Loss=0.004158003721386194 Batch_id=468 Accuracy=99.25: 100%|██████████| 469/469 [00:18<00:00, 25.08it/s]
        Test set: Average loss: 0.0203, Accuracy: 9938/10000 (99.38%)

    EPOCH: 11
    Loss=0.003466661088168621 Batch_id=468 Accuracy=99.20: 100%|██████████| 469/469 [00:18<00:00, 25.77it/s]
        Test set: Average loss: 0.0199, Accuracy: 9932/10000 (99.32%)

    EPOCH: 12
    Loss=0.0140219172462821 Batch_id=468 Accuracy=99.33: 100%|██████████| 469/469 [00:18<00:00, 25.75it/s]
        Test set: Average loss: 0.0190, Accuracy: 9939/10000 (99.39%)

    EPOCH: 13
    Loss=0.01336562167853117 Batch_id=468 Accuracy=99.32: 100%|██████████| 469/469 [00:17<00:00, 26.35it/s]
        Test set: Average loss: 0.0178, Accuracy: 9952/10000 (99.52%)

    EPOCH: 14
    Loss=0.009256711229681969 Batch_id=468 Accuracy=99.34: 100%|██████████| 469/469 [00:18<00:00, 25.92it/s]
        Test set: Average loss: 0.0182, Accuracy: 9951/10000 (99.51%)
        
        
 ![image](https://user-images.githubusercontent.com/70502759/213736485-9b943a08-2ac0-4158-8bae-88823c67a94d.png)


           

Step 4 :
   
    1 - Changes done: 
     
        1 - Image augmentation can help us generate more data set , hence we have
         added rotation to the image
        2 - Try LR Scheduler to Achive High Accuracy

             Model Summary : 

    ----------------------------------------------------------------
        Layer (type)               Output Shape         Param #
    ================================================================
            Conv2d-1           [-1, 15, 26, 26]             135
       BatchNorm2d-2           [-1, 15, 26, 26]              30
              ReLU-3           [-1, 15, 26, 26]               0
            Conv2d-4           [-1, 10, 24, 24]           1,350
       BatchNorm2d-5           [-1, 10, 24, 24]              20
              ReLU-6           [-1, 10, 24, 24]               0
            Conv2d-7           [-1, 16, 22, 22]           1,440
       BatchNorm2d-8           [-1, 16, 22, 22]              32
              ReLU-9           [-1, 16, 22, 22]               0
          Dropout-10           [-1, 16, 22, 22]               0
        MaxPool2d-11           [-1, 16, 11, 11]               0
           Conv2d-12           [-1, 20, 11, 11]             320
      BatchNorm2d-13           [-1, 20, 11, 11]              40
             ReLU-14           [-1, 20, 11, 11]               0
           Conv2d-15             [-1, 10, 9, 9]           1,800
      BatchNorm2d-16             [-1, 10, 9, 9]              20
             ReLU-17             [-1, 10, 9, 9]               0
           Conv2d-18             [-1, 10, 7, 7]             900
      BatchNorm2d-19             [-1, 10, 7, 7]              20
             ReLU-20             [-1, 10, 7, 7]               0
          Dropout-21             [-1, 10, 7, 7]               0
           Conv2d-22             [-1, 10, 5, 5]             900
      BatchNorm2d-23             [-1, 10, 5, 5]              20
             ReLU-24             [-1, 10, 5, 5]               0
        AvgPool2d-25             [-1, 10, 1, 1]               0
    ================================================================
    Total params: 7,027
    Trainable params: 7,027
    Non-trainable params: 0
    ----------------------------------------------------------------
    Input size (MB): 0.00
    Forward/backward pass size (MB): 0.71
    Params size (MB): 0.03
    Estimated Total Size (MB): 0.74
    ----------------------------------------------------------------
   

    2 - Results:

        1 - Parameters: 8k
        2 - Best Train Accuracy: 99.32 (At EPOCH - 14 , StepLR step_size=2, gamma=0.6)
        3 - Best Test Accuracy: 99.46  (At EPOCH - 11 , StepLR step_size=2, gamma=0.6)

    3 - Inference: 
     
     1- The model is under-fitting now. This is fine, as we know we have made
        our train data harder by adding image augmentation
     
     2 - The test accuracy is also up, which means our test data had few images
         which had transformation difference w.r.t. train dataset . 
     
     3 - The test  accuracy is not consistent across the different nearby epoch.
         This we have fix by tweaking the value of learning rate .
     
     4-  Finding a good LR schedule is hard.
         Initially we tried with learning rate 0. 01 . Above Learning rate with
         Scheduler help us to achieve the highest train accuracy of 99.10 and
         test accuracy of 99.39. As training accuracy is less if we can somehow
         increase this accuracy then overall model accuracy on test data can 
         also be increased .Hence we have started exploring with learning rate
         0. 1 . We have tried to make it effective by  reducing LR by 0.6 after
         the 2th  epoch.  Above Learning rate with Scheduler help us to achieve
         the highest test  accuracy of 99.46.
 
     5- The model shows consistant 99.4% accuracy for last few epochs
     
   4 - few traing logs 
       
           EPOCH: 9
    Loss=0.057361483573913574 Batch_id=468 Accuracy=99.18: 100%|██████████| 469/469 [00:17<00:00, 27.16it/s]
    Test set: Average loss: 0.0216, Accuracy: 9936/10000 (99.36%)

    EPOCH: 10
    Loss=0.02381567843258381 Batch_id=468 Accuracy=99.20: 100%|██████████| 469/469 [00:17<00:00, 27.19it/s]
    Test set: Average loss: 0.0204, Accuracy: 9944/10000 (99.44%)

    EPOCH: 11
    Loss=0.01638067327439785 Batch_id=468 Accuracy=99.23: 100%|██████████| 469/469 [00:17<00:00, 26.77it/s]
    Test set: Average loss: 0.0186, Accuracy: 9945/10000 (99.45%)

    EPOCH: 12
    Loss=0.03239172324538231 Batch_id=468 Accuracy=99.22: 100%|██████████| 469/469 [00:17<00:00, 27.24it/s]
    Test set: Average loss: 0.0201, Accuracy: 9938/10000 (99.38%)

    EPOCH: 13
    Loss=0.016828304156661034 Batch_id=468 Accuracy=99.20: 100%|██████████| 469/469 [00:17<00:00, 26.57it/s]
    Test set: Average loss: 0.0200, Accuracy: 9939/10000 (99.39%)

    EPOCH: 14
    Loss=0.0031423012260347605 Batch_id=468 Accuracy=99.27: 100%|██████████| 469/469 [00:18<00:00, 25.20it/s]
    Test set: Average loss: 0.0194, Accuracy: 9941/10000 (99.41%)

![image](https://user-images.githubusercontent.com/70502759/213739071-b817e8d0-5e6b-4f35-8d76-bbd96cb613e8.png)

  

## Tech Stack

Client: Python, Pytorch, Numpy

  
