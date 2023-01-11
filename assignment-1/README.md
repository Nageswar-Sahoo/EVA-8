
# Design Below Neural Network Architecture

   take 2 inputs:
 
     an image from the MNIST dataset (say 5), and
     a random number between 0 and 9, (say 7)
   
   and gives two outputs:
 
    the "number" that was represented by the MNIST image (predict 5), and
    the "sum" of this number with the random number and the input image to the network (predict 5 + 7 = 12)

![image](https://user-images.githubusercontent.com/70502759/136892002-fa6fad37-bab3-4f82-8a48-ef43557526b8.png)


 Input Data

  MNIST Image
   


  ![image](https://user-images.githubusercontent.com/70502759/136895005-4cb01984-b509-43cc-935b-7722036b413b.png)
  
  
  Random Number
  
  We have generate the random number dynamically with the help of following function by giving the batchsize 
     
     from random import randint
     randint(0,9)        
     
     [9, 0, 3, 7, 8, 5, 4, 1, 2, 6]
      
     

    
      
We have input image of shape (1,28,28), where 28*28 is height and  weidht of the image and  we have only one channel as it's a gray image 
We have a single random number which we have to add with the MNIST image number and will try to predicate the respective sum . 


Random Number converted to the one hot vector which can be used as an input to the neural network .

       [[0, 0, 0, 0, 0, 0, 0, 0, 0, 1],
        [1, 0, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 1, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 1, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0, 1, 0],
        [0, 0, 0, 0, 0, 1, 0, 0, 0, 0],
        [0, 0, 0, 0, 1, 0, 0, 0, 0, 0],
        [0, 1, 0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 1, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 1, 0, 0, 0]]

 


As we can predicate the maximum sum as 18 so including zero we have a total 19 class of prediction for the sum and 10 class of prediction for mnist number and total class is 29. We have prepared the actual labels that can be used for loss calculation after the model predicted handwritten mnist number and sum.


      
    Actual Mnist Number 
      [9, 0, 0, 3, 0, 2, 7, 2, 5, 5]       
    Random Number
      [9, 0, 3, 7, 8, 5, 4, 1, 2, 6]

    One Hot Represenatation 
       [[0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
        [1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
        [1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
        [0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0.],
        [1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
        [0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
        [0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0.],
        [0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
        [0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
        [0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 0., 0., 0.]])


Model Summery
   
![image](https://user-images.githubusercontent.com/70502759/211008908-3b311018-f0d9-4b19-875b-a1fa29275c2e.png)


Combined The Two Inputs

 Initially we have passed through  conv layers   and we have extracted the feature map. We have passed feature map into linear neural layer of output size(input 120, output 20) .  Random number we have passed through one Linear neural layer of output size(input 10,output 20) and concatenated both the outputs(20+20)and passed through linear layer  which resulted in output size (input 40,output 20) one dimension vector . Again this passed through two linear layer and give the two output of one representing the number prediction and other prediction is addition with random number . Hence model forward function return 2 output .



Loss function

 Since this is a classification problem, the choice of loss function may seem obvious – the CrossEntropy loss . 


Prediction at initial Layer : 

![image](https://user-images.githubusercontent.com/70502759/211008290-6c388c9a-d501-4ec1-aaf5-41665461e17a.png)

![image](https://user-images.githubusercontent.com/70502759/211008386-577eb923-ed14-4492-ab4d-f50a37d0bd99.png)


Prediction at final Layer : 

![image](https://user-images.githubusercontent.com/70502759/211008613-2b287a94-ed45-49d5-9930-b6ea9810b4a5.png)


After 10 epoch of training :

Iterations vs Loss:

![image](https://user-images.githubusercontent.com/70502759/211010939-610f6944-0a06-40f6-a479-be25acb13c7c.png)


Iterations vs Accuracy Number:

![image](https://user-images.githubusercontent.com/70502759/211010971-fbdc67a4-cd59-429d-978c-fe2698bfe879.png)



Iterations vs Accuracy Number Addition:

![image](https://user-images.githubusercontent.com/70502759/211011025-dc89d193-b590-44d5-b8cf-d3010be95ba3.png)
   

After 100 epoch of training :
Iterations vs Loss:

![image](https://user-images.githubusercontent.com/70502759/211009525-8b626097-7204-45bd-9667-39a9f2fb6c5d.png)

Iterations vs Accuracy Number:

![image](https://user-images.githubusercontent.com/70502759/211009627-951347f0-4d94-415a-8a32-f09a413eaf1b.png)

Iterations vs Accuracy Number Addition:

![image](https://user-images.githubusercontent.com/70502759/211009686-5bcf29f0-1a1b-4e6d-87c6-0cca41f88fdc.png)


Training Logs

               Iteration: 500, Loss: 0.9314156770706177, Accuracy Number: 98.8414306640625% , Accuracy Addition: 69.11856842041016%
               Iteration: 1000, Loss: 0.6620985865592957, Accuracy Number: 98.93000030517578% , Accuracy Addition: 73.67285919189453%
               Iteration: 1500, Loss: 0.68128901720047, Accuracy Number: 98.53428649902344% , Accuracy Addition: 70.30428314208984%
               Iteration: 2000, Loss: 0.5214945077896118, Accuracy Number: 99.19857025146484% , Accuracy Addition: 79.79285430908203%
               Iteration: 2500, Loss: 0.2817572057247162, Accuracy Number: 99.0528564453125% , Accuracy Addition: 80.6385726928711%
               Iteration: 3000, Loss: 0.29841065406799316, Accuracy Number: 99.15428924560547% , Accuracy Addition: 81.355712890625%
               Iteration: 3500, Loss: 0.022083772346377373, Accuracy Number: 98.4942855834961% , Accuracy Addition: 22.644285202026367%
               Iteration: 4000, Loss: 0.23250959813594818, Accuracy Number: 99.42428588867188% , Accuracy Addition: 83.65142822265625%
               Iteration: 4500, Loss: 0.1914070099592209, Accuracy Number: 99.34000396728516% , Accuracy Addition: 83.8614273071289%
               Iteration: 5000, Loss: 0.12673422694206238, Accuracy Number: 99.08142852783203% , Accuracy Addition: 82.68000030517578%
               Iteration: 5500, Loss: 0.29423099756240845, Accuracy Number: 99.52428436279297% , Accuracy Addition: 84.87142944335938%
               Iteration: 6000, Loss: 0.06285329163074493, Accuracy Number: 99.44857025146484% , Accuracy Addition: 84.99285888671875%
               Iteration: 6500, Loss: 0.07351688295602798, Accuracy Number: 99.40428924560547% , Accuracy Addition: 84.7414321899414%
               Iteration: 7000, Loss: 0.009202642366290092, Accuracy Number: 99.0442886352539% , Accuracy Addition: 22.63857078552246%
               Iteration: 7500, Loss: 0.14904536306858063, Accuracy Number: 99.59000396728516% , Accuracy Addition: 85.71142578125%
               Iteration: 8000, Loss: 0.08631718903779984, Accuracy Number: 99.51285552978516% , Accuracy Addition: 85.42713928222656%
               Iteration: 8500, Loss: 0.09643895924091339, Accuracy Number: 99.29856872558594% , Accuracy Addition: 84.82571411132812%
               Iteration: 9000, Loss: 0.22589130699634552, Accuracy Number: 99.5442886352539% , Accuracy Addition: 85.80999755859375%
               Iteration: 9500, Loss: 0.03228733316063881, Accuracy Number: 99.644287109375% , Accuracy Addition: 85.86856842041016%
               Iteration: 10000, Loss: 0.05785221979022026, Accuracy Number: 99.45714569091797% , Accuracy Addition: 85.47714233398438%
               Iteration: 10500, Loss: 0.02513701841235161, Accuracy Number: 99.04856872558594% , Accuracy Addition: 22.644285202026367%
               Iteration: 11000, Loss: 0.12709052860736847, Accuracy Number: 99.6642837524414% , Accuracy Addition: 86.13143157958984%
               Iteration: 11500, Loss: 0.05918920785188675, Accuracy Number: 99.61714172363281% , Accuracy Addition: 85.75142669677734%
               Iteration: 12000, Loss: 0.05909654125571251, Accuracy Number: 99.32428741455078% , Accuracy Addition: 84.93285369873047%
               Iteration: 12500, Loss: 0.1677832305431366, Accuracy Number: 99.66143035888672% , Accuracy Addition: 86.0142822265625%
               Iteration: 13000, Loss: 0.01705341227352619, Accuracy Number: 99.6971435546875% , Accuracy Addition: 86.05000305175781%
               Iteration: 13500, Loss: 0.07127616554498672, Accuracy Number: 99.45714569091797% , Accuracy Addition: 85.4142837524414%
               Iteration: 14000, Loss: 0.0393061637878418, Accuracy Number: 98.95857238769531% , Accuracy Addition: 22.644285202026367%
               Iteration: 14500, Loss: 0.07729607075452805, Accuracy Number: 99.67713928222656% , Accuracy Addition: 86.13714599609375%
               Iteration: 15000, Loss: 0.05898115038871765, Accuracy Number: 99.57571411132812% , Accuracy Addition: 85.68571472167969%
               Iteration: 15500, Loss: 0.03328073397278786, Accuracy Number: 99.42285919189453% , Accuracy Addition: 85.20999908447266%
               Iteration: 16000, Loss: 0.1216244325041771, Accuracy Number: 99.69571685791016% , Accuracy Addition: 86.29285430908203%
               Iteration: 16500, Loss: 0.01775733195245266, Accuracy Number: 99.54856872558594% , Accuracy Addition: 85.91857147216797%
               Iteration: 17000, Loss: 0.07438291609287262, Accuracy Number: 99.57428741455078% , Accuracy Addition: 85.98999786376953%
               Iteration: 17500, Loss: 0.002895275829359889, Accuracy Number: 99.19285583496094% , Accuracy Addition: 22.648571014404297%
               Iteration: 18000, Loss: 0.03748469427227974, Accuracy Number: 99.69857025146484% , Accuracy Addition: 86.27571105957031%
               Iteration: 18500, Loss: 0.10480452328920364, Accuracy Number: 99.55999755859375% , Accuracy Addition: 85.72571563720703%
               Iteration: 19000, Loss: 0.08406321704387665, Accuracy Number: 99.23285675048828% , Accuracy Addition: 84.89714050292969%
               Iteration: 19500, Loss: 0.04625723883509636, Accuracy Number: 99.76000213623047% , Accuracy Addition: 86.25286102294922%
               Iteration: 20000, Loss: 0.019652465358376503, Accuracy Number: 99.70999908447266% , Accuracy Addition: 86.17428588867188%
               Iteration: 20500, Loss: 0.09637583047151566, Accuracy Number: 99.51142883300781% , Accuracy Addition: 85.7028579711914%
               Iteration: 21000, Loss: 0.00898099783807993, Accuracy Number: 99.1500015258789% , Accuracy Addition: 22.654285430908203%
               Iteration: 21500, Loss: 0.05729310214519501, Accuracy Number: 99.76142883300781% , Accuracy Addition: 86.40142822265625%
               Iteration: 22000, Loss: 0.07854355871677399, Accuracy Number: 99.7300033569336% , Accuracy Addition: 86.08714294433594%
               Iteration: 22500, Loss: 0.11822915822267532, Accuracy Number: 99.31428527832031% , Accuracy Addition: 85.06143188476562%
               Iteration: 23000, Loss: 0.040171921253204346, Accuracy Number: 99.78428649902344% , Accuracy Addition: 86.31857299804688%
               Iteration: 23500, Loss: 0.024322394281625748, Accuracy Number: 99.7442855834961% , Accuracy Addition: 86.22571563720703%
               Iteration: 24000, Loss: 0.052925169467926025, Accuracy Number: 99.64142608642578% , Accuracy Addition: 86.00286102294922%
               Iteration: 24500, Loss: 0.00957380048930645, Accuracy Number: 99.21571350097656% , Accuracy Addition: 22.648571014404297%
               Iteration: 25000, Loss: 0.034360237419605255, Accuracy Number: 99.75% , Accuracy Addition: 86.43285369873047%
               Iteration: 25500, Loss: 0.07828138023614883, Accuracy Number: 99.69285583496094% , Accuracy Addition: 85.9942855834961%
               Iteration: 26000, Loss: 0.08374898135662079, Accuracy Number: 99.32857513427734% , Accuracy Addition: 84.89286041259766%
               Iteration: 26500, Loss: 0.027417737990617752, Accuracy Number: 99.81857299804688% , Accuracy Addition: 86.44000244140625%
               Iteration: 27000, Loss: 0.012373438104987144, Accuracy Number: 99.7442855834961% , Accuracy Addition: 86.28571319580078%
               Iteration: 27500, Loss: 0.0401529036462307, Accuracy Number: 99.53857421875% , Accuracy Addition: 85.9671401977539%
               Iteration: 28000, Loss: 0.017585765570402145, Accuracy Number: 99.18142700195312% , Accuracy Addition: 22.667142868041992%
               Iteration: 28500, Loss: 0.0608706995844841, Accuracy Number: 99.82571411132812% , Accuracy Addition: 86.61285400390625%
               Iteration: 29000, Loss: 0.04506314545869827, Accuracy Number: 99.7557144165039% , Accuracy Addition: 86.33856964111328%
               Iteration: 29500, Loss: 0.0625610500574112, Accuracy Number: 99.2699966430664% , Accuracy Addition: 85.11285400390625%
               Iteration: 30000, Loss: 0.022832652553915977, Accuracy Number: 99.81428527832031% , Accuracy Addition: 86.51571655273438%
               Iteration: 30500, Loss: 0.018253615126013756, Accuracy Number: 99.73999786376953% , Accuracy Addition: 86.25286102294922%
               Iteration: 31000, Loss: 0.05696195363998413, Accuracy Number: 99.67428588867188% , Accuracy Addition: 86.04000091552734%
               Iteration: 31500, Loss: 0.012451176531612873, Accuracy Number: 99.2442855834961% , Accuracy Addition: 22.645713806152344%
               Iteration: 32000, Loss: 0.03634081780910492, Accuracy Number: 99.8499984741211% , Accuracy Addition: 86.57857513427734%
               Iteration: 32500, Loss: 0.05982573330402374, Accuracy Number: 99.6914291381836% , Accuracy Addition: 86.30000305175781%
               Iteration: 33000, Loss: 0.04927965998649597, Accuracy Number: 99.44999694824219% , Accuracy Addition: 85.45857238769531%
               Iteration: 33500, Loss: 0.010236183181405067, Accuracy Number: 99.81428527832031% , Accuracy Addition: 86.61000061035156%
               Iteration: 34000, Loss: 0.022407954558730125, Accuracy Number: 99.80714416503906% , Accuracy Addition: 86.5142822265625%
               Iteration: 34500, Loss: 0.02733747288584709, Accuracy Number: 99.72856903076172% , Accuracy Addition: 86.1500015258789%
               Iteration: 35000, Loss: 0.006501208525151014, Accuracy Number: 99.10285949707031% , Accuracy Addition: 22.695714950561523%
               Iteration: 35500, Loss: 0.029189186170697212, Accuracy Number: 99.82571411132812% , Accuracy Addition: 86.54285430908203%
               Iteration: 36000, Loss: 0.07513110339641571, Accuracy Number: 99.78713989257812% , Accuracy Addition: 86.41999816894531%
               Iteration: 36500, Loss: 0.13083527982234955, Accuracy Number: 99.23857116699219% , Accuracy Addition: 84.77714538574219%
               Iteration: 37000, Loss: 0.024114537984132767, Accuracy Number: 99.84571075439453% , Accuracy Addition: 86.44428253173828%
               Iteration: 37500, Loss: 0.040876127779483795, Accuracy Number: 99.82571411132812% , Accuracy Addition: 86.50714111328125%
               Iteration: 38000, Loss: 0.06071210652589798, Accuracy Number: 99.58285522460938% , Accuracy Addition: 85.8614273071289%
               Iteration: 38500, Loss: 0.0027029295451939106, Accuracy Number: 99.31714630126953% , Accuracy Addition: 22.670000076293945%
               Iteration: 39000, Loss: 0.029690023511648178, Accuracy Number: 99.86428833007812% , Accuracy Addition: 86.61856842041016%
               Iteration: 39500, Loss: 0.09625431895256042, Accuracy Number: 99.79000091552734% , Accuracy Addition: 86.44857025146484%
               Iteration: 40000, Loss: 0.035070862621068954, Accuracy Number: 99.44428253173828% , Accuracy Addition: 85.28713989257812%
               Iteration: 40500, Loss: 0.022228576242923737, Accuracy Number: 99.84285736083984% , Accuracy Addition: 86.6500015258789%
               Iteration: 41000, Loss: 0.014648946933448315, Accuracy Number: 99.81999969482422% , Accuracy Addition: 86.52714538574219%
               Iteration: 41500, Loss: 0.14566870033740997, Accuracy Number: 99.58285522460938% , Accuracy Addition: 85.95143127441406%
               Iteration: 42000, Loss: 0.008903741836547852, Accuracy Number: 99.32714080810547% , Accuracy Addition: 22.687143325805664%
               Iteration: 42500, Loss: 0.04445037990808487, Accuracy Number: 99.88571166992188% , Accuracy Addition: 86.79285430908203%
               Iteration: 43000, Loss: 0.0645759254693985, Accuracy Number: 99.8499984741211% , Accuracy Addition: 86.44428253173828%
               Iteration: 43500, Loss: 0.02786724828183651, Accuracy Number: 99.44999694824219% , Accuracy Addition: 85.68856811523438%
               Iteration: 44000, Loss: 0.009152541868388653, Accuracy Number: 99.90428924560547% , Accuracy Addition: 86.88143157958984%
               Iteration: 44500, Loss: 0.01786447875201702, Accuracy Number: 99.81857299804688% , Accuracy Addition: 86.5971450805664%
               Iteration: 45000, Loss: 0.02661374770104885, Accuracy Number: 99.74285888671875% , Accuracy Addition: 86.31143188476562%
               Iteration: 45500, Loss: 0.005523106548935175, Accuracy Number: 99.34857177734375% , Accuracy Addition: 22.658571243286133%
               Iteration: 46000, Loss: 0.03148198127746582, Accuracy Number: 99.86285400390625% , Accuracy Addition: 86.68285369873047%
               Iteration: 46500, Loss: 0.09397920221090317, Accuracy Number: 99.84428405761719% , Accuracy Addition: 86.54285430908203%
               Iteration: 47000, Loss: 0.016182806342840195, Accuracy Number: 99.4914321899414% , Accuracy Addition: 85.4800033569336%
               Iteration: 47500, Loss: 0.013392004184424877, Accuracy Number: 99.91571807861328% , Accuracy Addition: 86.84571075439453%
               Iteration: 48000, Loss: 0.020608430728316307, Accuracy Number: 99.84571075439453% , Accuracy Addition: 86.67285919189453%
               Iteration: 48500, Loss: 0.021692251786589622, Accuracy Number: 99.7057113647461% , Accuracy Addition: 86.38143157958984%
               Iteration: 49000, Loss: 0.014338488690555096, Accuracy Number: 99.07857513427734% , Accuracy Addition: 22.674285888671875%
               Iteration: 49500, Loss: 0.057508066296577454, Accuracy Number: 99.87714385986328% , Accuracy Addition: 86.7828598022461%
               Iteration: 50000, Loss: 0.043668363243341446, Accuracy Number: 99.82714080810547% , Accuracy Addition: 86.61285400390625%
               Iteration: 50500, Loss: 0.04627334699034691, Accuracy Number: 99.4942855834961% , Accuracy Addition: 85.58285522460938%
               Iteration: 51000, Loss: 0.01060036662966013, Accuracy Number: 99.92571258544922% , Accuracy Addition: 86.87000274658203%
               Iteration: 51500, Loss: 0.025639258325099945, Accuracy Number: 99.86571502685547% , Accuracy Addition: 86.77285766601562%
               Iteration: 52000, Loss: 0.03669574484229088, Accuracy Number: 99.73285675048828% , Accuracy Addition: 86.27285766601562%
               Iteration: 52500, Loss: 0.00962761975824833, Accuracy Number: 99.3471450805664% , Accuracy Addition: 22.654285430908203%
               Iteration: 53000, Loss: 0.04836989939212799, Accuracy Number: 99.894287109375% , Accuracy Addition: 86.81999969482422%
               Iteration: 53500, Loss: 0.04389121010899544, Accuracy Number: 99.79285430908203% , Accuracy Addition: 86.61428833007812%
               Iteration: 54000, Loss: 0.07858822494745255, Accuracy Number: 99.41143035888672% , Accuracy Addition: 85.57714080810547%
               Iteration: 54500, Loss: 0.007837045937776566, Accuracy Number: 99.92571258544922% , Accuracy Addition: 86.91571807861328%
               Iteration: 55000, Loss: 0.021815268322825432, Accuracy Number: 99.8357162475586% , Accuracy Addition: 86.68285369873047%



## Tech Stack

**Client:** Python, Pytorch, Numpy


  
