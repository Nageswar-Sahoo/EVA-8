# Problem Statement 

[Check out this](https://canvas.instructure.com/courses/5720700/assignments/35712640?module_item_id=80543490#:~:text=Check%20out%20this-,network,Links%20to%20an%20external%20site.,-%3A)

    Re-write this network such that it is similar to the network we wrote in the class
    All parameters are the same as the network we wrote
    Proceed to submit the assignment:
    Share the model code and link to the model cost
    Share the training logs
    Share the gradcam images for 10 misclassified images

Training logs :

   ConvMixer: Epoch: 0 | Train Acc: 0.2113, Test Acc: 0.3401, Time: 63.5, lr: 0.001000
   ConvMixer: Epoch: 1 | Train Acc: 0.3549, Test Acc: 0.4517, Time: 56.7, lr: 0.002000
   ConvMixer: Epoch: 2 | Train Acc: 0.4503, Test Acc: 0.5340, Time: 58.8, lr: 0.003000
   ConvMixer: Epoch: 3 | Train Acc: 0.4976, Test Acc: 0.5534, Time: 58.8, lr: 0.004000
   ConvMixer: Epoch: 4 | Train Acc: 0.5192, Test Acc: 0.5637, Time: 57.2, lr: 0.005000
   ConvMixer: Epoch: 5 | Train Acc: 0.5384, Test Acc: 0.5985, Time: 60.6, lr: 0.006000
   ConvMixer: Epoch: 6 | Train Acc: 0.5482, Test Acc: 0.5960, Time: 58.3, lr: 0.007000
   ConvMixer: Epoch: 7 | Train Acc: 0.5612, Test Acc: 0.6031, Time: 57.8, lr: 0.008000
   ConvMixer: Epoch: 8 | Train Acc: 0.5714, Test Acc: 0.6128, Time: 58.7, lr: 0.009000
   ConvMixer: Epoch: 9 | Train Acc: 0.5854, Test Acc: 0.6298, Time: 57.5, lr: 0.010000
   ConvMixer: Epoch: 10 | Train Acc: 0.5947, Test Acc: 0.6266, Time: 58.2, lr: 0.009050
   ConvMixer: Epoch: 11 | Train Acc: 0.6161, Test Acc: 0.6650, Time: 57.9, lr: 0.008100
   ConvMixer: Epoch: 12 | Train Acc: 0.6343, Test Acc: 0.6699, Time: 58.1, lr: 0.007150
   ConvMixer: Epoch: 13 | Train Acc: 0.6542, Test Acc: 0.6888, Time: 58.0, lr: 0.006200
   ConvMixer: Epoch: 14 | Train Acc: 0.6728, Test Acc: 0.7074, Time: 58.7, lr: 0.005250
   ConvMixer: Epoch: 15 | Train Acc: 0.6854, Test Acc: 0.7390, Time: 59.3, lr: 0.004300
   ConvMixer: Epoch: 16 | Train Acc: 0.7035, Test Acc: 0.7308, Time: 60.0, lr: 0.003350
   ConvMixer: Epoch: 17 | Train Acc: 0.7140, Test Acc: 0.7463, Time: 56.1, lr: 0.002400
   ConvMixer: Epoch: 18 | Train Acc: 0.7297, Test Acc: 0.7570, Time: 54.6, lr: 0.001450
   ConvMixer: Epoch: 19 | Train Acc: 0.7446, Test Acc: 0.7709, Time: 55.3, lr: 0.000500
   ConvMixer: Epoch: 20 | Train Acc: 0.7522, Test Acc: 0.7784, Time: 55.3, lr: 0.000400
   ConvMixer: Epoch: 21 | Train Acc: 0.7558, Test Acc: 0.7776, Time: 55.4, lr: 0.000300
   ConvMixer: Epoch: 22 | Train Acc: 0.7563, Test Acc: 0.7825, Time: 54.6, lr: 0.000200
   ConvMixer: Epoch: 23 | Train Acc: 0.7623, Test Acc: 0.7783, Time: 53.5, lr: 0.000100
   ConvMixer: Epoch: 24 | Train Acc: 0.7628, Test Acc: 0.7803, Time: 54.2, lr: 0.000000
   
Misclassified and GradCam Images Gallery

Misclassified images were generated and for each misclassified image a gradcam image was generated for the misclassified class the model predicted.


![image](https://user-images.githubusercontent.com/70502759/144750833-5887da41-3d00-4eaa-8d2f-3bac2d70ccb0.png)
![image](https://user-images.githubusercontent.com/70502759/144750838-d795c34f-8590-4de3-9fba-ee4ed620d2e5.png)
![image](https://user-images.githubusercontent.com/70502759/144750844-e68b89d1-9776-47a6-be81-9efa55111ca7.png)
![image](https://user-images.githubusercontent.com/70502759/144750854-d32b9b2e-2369-4fce-9608-505738652bc5.png)
![image](https://user-images.githubusercontent.com/70502759/144750856-ab330c0a-94f7-4efc-9bc1-dcd79ef1de47.png)
![image](https://user-images.githubusercontent.com/70502759/144750861-4cda47d5-7829-436b-bee4-7d8a0f277627.png)
![image](https://user-images.githubusercontent.com/70502759/144750868-bf58d25f-16b3-43af-ba3d-ef7e106efc1b.png)
![image](https://user-images.githubusercontent.com/70502759/144750873-23fd16bd-9ae7-4737-8040-752754615c00.png)
![image](https://user-images.githubusercontent.com/70502759/144750874-54e896fc-4195-4f37-8661-7b2b272c25d1.png)
![image](https://user-images.githubusercontent.com/70502759/144750878-a904a374-4d38-43a6-8264-a9d6124316a7.png)
![image](https://user-images.githubusercontent.com/70502759/144750884-1191ccd3-0d26-41dd-b922-8ddcd4931314.png)
![image](https://user-images.githubusercontent.com/70502759/144750895-13b1c01d-a895-4fca-a15d-537f23c5cf28.png)
![image](https://user-images.githubusercontent.com/70502759/144750899-e3026fb8-ccac-4dc5-968a-5aebaf000faf.png)
![image](https://user-images.githubusercontent.com/70502759/144750908-3517ba1c-bbd4-4997-a0e7-0147616f8766.png)
![image](https://user-images.githubusercontent.com/70502759/144750911-97347a52-7d53-46db-9abe-820c7a7aa576.png)
![image](https://user-images.githubusercontent.com/70502759/144750927-d33bc7e4-c331-4d79-81d2-1ca0105e8a47.png)
![image](https://user-images.githubusercontent.com/70502759/144750931-47408f19-c785-4d77-92ba-aa0228a97c59.png)
![image](https://user-images.githubusercontent.com/70502759/144750939-8e0c9c8a-2918-406e-ae6c-dd80f689362b.png)
![image](https://user-images.githubusercontent.com/70502759/144750944-f9994bd4-443f-4498-bcd8-f86b21a26be6.png)
![image](https://user-images.githubusercontent.com/70502759/144750950-66065d8a-1962-45cf-a708-e814093eeab1.png)



 


