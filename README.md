# Phase 4 Project: Computer Vision for Detecting Pneumonia in X-Ray Images
**Sam Lim** <br>
**James Irving** <br>
**First Presentation: 6/25/21** <br>

![main header](images/front.JPG)

## Contents

 - <a href='#BusinessProblem'> Business Problem </a>
 - <a href='#Preprocessing'> Preprocessing </a>
 - <a href='#DataModeling'> Data Modeling</a>
 - <a href='#Recommendation'> Recommendation </a>
 - <a href='#Conclusion'> Conclusion </a>

 
<a id='BusinessProblem'></a>
## Business Problem

Due to a shortage of staff and doctors through COVID-19, the St.Jude Children's Hospital wants to use A.I. to diagnose pneumonia through x-ray images of children's lungs. The goal of this project is to use convolution neural network for computer vision to detect pneumonia from x-ray images.

<a id='Preprocessing'></a>
## Preprocessing
In order for the neural network to be able to read and understand images, I used the ImageDataGenerator from tensorflow.keras. Each pixel's RGB value was divided by 255 so that they ranged from 0 to 1. Also, because the provided validation set was too small, I had to split the test set to create a new validation set.<br>
![dataprep](images/dataprep.JPG)<br>
The image on the left shows a normal chest x-ray and the right shows pneumonia chest x-ray<br>
<div>
    <img src='data/train/NORMAL/IM-0115-0001.jpeg' width='340'/>
    <img src='data/train/PNEUMONIA/person1_bacteria_2.jpeg' width='340'/>
</div>
Such images above are then downsized to 64 x 64 pixel images<br>
![small1](images/xray1.JPG)
![small2](images/xray2.JPG)


<a id='DataModeling'></a>
## Data Modeling
Using Convolutional Neural Network(CNN), I initially created 10 convolutional layers, 5 maxpooling layers, and 3 dense layers. All iterations used adam as the optimizer, binary crossentropy as the loss function and binary accuracy as the main metric. Each iteration had two versions; the first version used the validation loss as the stopping metric and the other used validation accuracy as the stopping metric. Overall, using validation accuracy as the stopping metric created better models. The goal for each proceeding iteration was to reduce the number of overall layers while increasing/maintaining the overall accuracy of the model. <br>
The first set of images is the first iteration of the model that used validation loss as the stopping metric, and the second set is the same model using validation accuracy as the stopping metric. The graph clearly indicates that using the validation accuracy helped the overall fitness of the model.<br>
#### Model 1. Stopping metric = validation loss
<div>
    <img src='images/model1loss.JPG' width='340'/>
    <img src='images/model1losscm.JPG' width='340'/>
</div>
<br>
<div>
    <img src='images/model1acc.JPG' width='340'/>
    <img src='images/model1acccm.JPG' width='340'/>
</div>
<br>
The next two sets of the images are the third iteration of the model. The first set uses validation loss and the second uses validation accuracy as the stopping metric.
#### Model 3. Stopping metric = validation loss

<div>
    <img src='images/model3loss.JPG' width='340'/>
    <img src='images/model3losscm.JPG' width='340'/>
</div>
<br>
<div>
    <img src='images/model3acc.JPG' width='340'/>
    <img src='images/model3acccm.JPG' width='340'/>
</div>
<br>
There was a total of four iteration of the modeling process, but reducing the number of convolutional layers after a certain point impaired the overall model.

<a id='Recommendation'></a>
## Recommendation 
As can be observed from the above models, the version that uses validation accuracy had overall better performance. And comparing all iterations of the models, I would recommend the 3rd iteration of the model that uses validation accuracy as the stopping metric as it had a high recall score for the true positives and the highest score of true negatives. While other iterations had similar recall scores for the true positive, either their recall score for true negatives were lower or their graph showing the validation loss and validation accuracy did not fit properly.

<a id='Conclusion'></a>
## Conclusion 

### Future Work
For future work, I would like to improve the model's prediction on false positives. While it was very apt in diagnosing pneumonia for patients with pneumonia, it was as much likely to diagnose pneumonia to those who did not have the disease. Possible solutions may be:
 - Format/align the pictures to show just the thorax region to remove possible mis-detections
 - Distinguish sections such as the heart to remove possible mis-detections
 - Separate images of bacterial pneumonia and viral pneumonia for training for ease of diagnosis since they require different treatments. 

### Final Thoughts
Overall, the project was as challenging as it was insightful. After visiting an A.I. expo and seeing how computer vision was being used to diagnose cancer and how the A.I. that they had created were finding previously unknown indications that could lead to an early diagnosis of breast cancer. The year before this, the doctors had found a tumor-like tissue in her uterus during an annual check up. Fortunately it turned out to be a benign form, but we were worried that she could develop breast cancer as uterine tumors could lead to or were early signs of breast cancer. Because of this previous incident, the use of A.I. in diagnosing cancer spoke to me in a different way, and I became much interested in general A.I. and the use of A.I. in the medical field. Though this project is miles behind compared to what I had seen in the expo, it was meaningful nonetheless.

