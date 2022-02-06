
  
  
[//]: # (____________________________________PROJECT TITLE____________________________________)

<br>
<hr style="height:4px;border-width:10;color:blue;background-color:black">

<img src="img/logo2.png"  width="200" height="100" align="left">

<h1 >MonReader</h1>
<br />
<hr style="height:4px;border-width:10;color:blue;background-color:black">
<br><br><br>


[//]: # (____________________________________BACKGROUND____________________________________)

<img src="https://images.genial.ly/59e059d30b9c21060cb4c2ec/5bbf17763292ef649e9b810f/175cbb1e-df65-405a-9cd0-cf177e1a2f00.gif?genial&1633910400074" width="60" height="70" align="left">

## Background:
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">


Our company develops innovative Artificial Intelligence and Computer Vision solutions that revolutionize industries. Machines that can see: We pack our solutions in small yet intelligent devices that can be easily integrated to your existing data flow. Computer vision for everyone: Our devices can recognize faces, estimate age and gender, classify clothing types and colors, identify everyday objects and detect motion. Technical consultancy: We help you identify use cases of artificial intelligence and computer vision in your industry. Artificial intelligence is the technology of today, not the future.

MonReader is a new mobile document digitization experience for the blind, for researchers and for everyone else in need for fully automatic, highly fast and high-quality document scanning in bulk. It is composed of a mobile app and all the user needs to do is flip pages and everything is handled by MonReader: it detects page flips from low-resolution camera preview and takes a high-resolution picture of the document, recognizing its corners and crops it accordingly, and it dewarps the cropped document to obtain a bird's eye view, sharpens the contrast between the text and the background and finally recognizes the text with formatting kept intact, being further corrected by MonReader's ML powered redactor.

<br />
<div align="center"><img src="img/img1.png"  width="500px" height="500px"></div>

<br><br>

MonReader is a new mobile document digitalization experience for the blind, for researchers and for everyone else in need for fully automatic, highly fast and high-quality document scanning in bulk. It is composed of a mobile app and all the user needs to do is flip pages and everything is handled by MonReader: it detects page flips from low-resolution camera preview and takes a high-resolution picture of the document, recognizing its corners and crops it accordingly, and it dewarps the cropped document to obtain a bird's eye view, sharpens the contrast between the text and the background and finally recognizes the text with formatting kept intact, being further corrected by MonReader's ML powered redactor.

<br />
<div align="center"><img src="img/img2.jpg" width="500px" height="500px"></div>

<br><br>

[//]: # (____________________________________DATA DESCRIPTION____________________________________)


<img src="https://media.baamboozle.com/uploads/images/67969/1595412283_471863"  width="60" height="70" align="left">

## Data Description:
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">

We collected page flipping video from smart phones and labelled them as flipping and not flipping.

We clipped the videos as short videos and labelled them as flipping or not flipping. The extracted frames are then saved to disk in a sequential order with the following naming structure: VideoID_FrameNumber.

<br><br>


[//]: # (____________________________________ATTRIBUTES____________________________________)

<img src="https://c.tenor.com/1_5w5vXEH5gAAAAj/mandalorian-star-wars.gif" width="60" height="60" align="left">

## Goal(s)::
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">

Predict if the page is being flipped using a single image.

<br><br>


[//]: # (____________________________________PROJECT OVERVIEW____________________________________)


<img src="https://media0.giphy.com/media/LmqdA28jZ7bitDeDWr/200.webp"  width="60" height="60" align="left">

## Project Overview:
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">

### data preprocessing:

The original data set size was `1080 * 1920` pixels with two classes, `flip` and `notflip` class as in the following picture.

<div align="center"><img src="img/original_data.png"  width="600px" height="400px"></div>

As for the preprocessing, the data size was reduced to `100 * 70` pixels and scaling was applied by dividing the pixels by **225**. The result is shown in the next image.

<div align="center"><img src="img/preprocess_data.png"  width="600px" height="400px"></div><br>


### Modeling:

  - ### **1) Model Architecture**
      The model consists of 2 CNN layers, 2 Max Pooling layers with 2*2 and finally 2 dense layers.
      <div align="center"><img src="img/model.png"  width="600px" height="400px"></div><br>

  - ### **2) Training and Optimization**:
    The model was tested with different hyperparameters like:
      - `tanh` and `relu` as activation functions.
      - `0.0001`, `0.001` and `0.1` as a learning rate.

      All of the models accuracy and loss scores are shown in the following images:


      <div align="center"><img src="img/exp_1_acc_all.png"  width="700px" height="300"></div><br>

      <div align="center"><img src="img/exp_1_val_all.png"  width="700px" height="300"></div><br>


      In order to compare the models, I will compare them based on the learning rate. First of all, the loss scores with **0.0001** learning rate, we can see the loss decreased with the time gradually and the `thanh` activation function perform better than the `relu`. In the second image, we can see the loss score for the **0.001** learning rate. From the figure, it's clear that the `tanh` activation function exceeds the `relu`, not in the final score only but also in how fast it decreased. And in the final image, the learning rate was the biggest one which is **0.1**. It's clear from the image, this is the worst learning rate for this data with both of `relu` and `tanh` activation functions.


      <div align="center"><img src="img/exp1_val_0.0001.png"  width="550px" height="350px"></div><br>

      <div align="center"><img src="img/exp1_val_0.001.png"  width="500px" height="300px"></div><br>

      <div align="center"><img src="img/exp1_val_0.01.png" width="500px" height="300px"></div><br>


      Therefore, both of **tanh** activation function and **0.001** learning rate was chosen for the final model. As we can see in the first image, the final accuracy score for the training images is `100%` and `99.9%` for the validation images. In the second picture, the training loss was `0.017` and `0.04` for validation images.


      <div align="center"><img src="img/final_model_acc.png"  width="500px" height="300px"></div><br>

      <div align="center"><img src="img/final_model_val.png"  width="500px" height="300px"></div><br>

      <br><br>
      
  - ### **3) Testing**
      The accuracy for the test data is `99.7%`, and the confusion matrix confirms that. It looks like the model performs slightly better in the `flip` class more than `not flip` and this is can be justified by the difference between the number of images in each class.


      <div align="center"><img src="img/test_confusion.png"  width="500px" height="300px"></div><br>




[//]: # (&#40;____________________________________ CONCLUSION____________________________________&#41;)

<img src="https://media4.giphy.com/media/MbMUCH4MUffka1ZFeT/giphy.gif?cid=790b7611040baf4e7332c491694685e3367d8fe931cd7a69&rid=giphy.gif&ct=s"  width="80" height="60" align="left">

## Conclusion:
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">

Different model hyperparameters were tested and in general, some of the models prefer well in the range of **10** epochs. From the training and optimization section, it's clear this data prefer a learning rate of around 0.001 and tanh activation function better than relu. Our best model test score is `99.7%` with a loss equal to `0.046`.

