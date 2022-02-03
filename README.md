
  
  
[//]: # (____________________________________PROJECT TITLE____________________________________)

<br>
<hr style="height:4px;border-width:10;color:blue;background-color:black">

<img src="img/logo2.png" alt="Smiley face" width="200" height="100" align="left">

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
<div align="center"><img src="img/img1.png" alt="Logo" width="500px" height="500px"></div>

<br><br>

MonReader is a new mobile document digitalization experience for the blind, for researchers and for everyone else in need for fully automatic, highly fast and high-quality document scanning in bulk. It is composed of a mobile app and all the user needs to do is flip pages and everything is handled by MonReader: it detects page flips from low-resolution camera preview and takes a high-resolution picture of the document, recognizing its corners and crops it accordingly, and it dewarps the cropped document to obtain a bird's eye view, sharpens the contrast between the text and the background and finally recognizes the text with formatting kept intact, being further corrected by MonReader's ML powered redactor.

<br />
<div align="center"><img src="img/img2.jpg" alt="Logo" width="500px" height="500px"></div>

<br><br>

[//]: # (____________________________________DATA DESCRIPTION____________________________________)


<img src="https://media.baamboozle.com/uploads/images/67969/1595412283_471863" alt="Smiley face" width="60" height="70" align="left">

## Data Description:
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">

We collected page flipping video from smart phones and labelled them as flipping and not flipping.

We clipped the videos as short videos and labelled them as flipping or not flipping. The extracted frames are then saved to disk in a sequential order with the following naming structure: VideoID_FrameNumber.

<br><br>


[//]: # (____________________________________ATTRIBUTES____________________________________)

<img src="https://c.tenor.com/1_5w5vXEH5gAAAAj/mandalorian-star-wars.gif" alt="Smiley face" width="60" height="60" align="left">

## Goal(s)::
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">

Predict if the page is being flipped using a single image.

<br><br>


[//]: # (____________________________________PROJECT OVERVIEW____________________________________)


<img src="https://media0.giphy.com/media/LmqdA28jZ7bitDeDWr/200.webp" alt="Smiley face" width="60" height="60" align="left">

## Project Overview:
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">

The original data set size was `1080 * 1920` pixels with two classes, `flip` and `notflip` class as in the following picture.

<div align="center"><img src="img/original_data.png" alt="Logo" width="600px" height="400px"></div>

As for the preprocessing, the data size was reduced to `100 * 70` pixels and scaling was applied by dividing the pixels by **225**. The result is shown in the next image.


<div align="center"><img src="img/preprocess_data.png" alt="Logo" width="600px" height="400px"></div>

For the model, different hyperparameters were tested like:
- `tanh` and `relu` as activation functions.
- `0.0001`, `0.001` and `0.1` as a learning rate.

All of the models accuracy and loss scores are shown in the following images:


<div align="center"><img src="img/acc_all.png" alt="Logo" width="700px" height="300"></div>

<div align="center"><img src="img/val_all.png" alt="Logo" width="700px" height="300"></div>


In order to compare the models, I divide them based on the learning rate. First of all, the loss scores with **0.0001** learning rate, we can see the loss decreased with the time gradually and the than activation function perform better than the relu. In the second image, we can see the loss score for the **0.001** learning rate. From the figure, it's clear that the tanh activation function exceeds the relu, not in the final score only but also in how fast it decreased. And in the final image, the learning rate was the biggest one which is **0.1**. As for the loss score, it's clear the relu is performed much better than tanh. With tanh activation function the model stopped improving at the 8ith epoch with **5** patients, which means the model stopped learning after the third epoch!


<div align="center"><img src="img/val_0.0001.png" alt="Logo" width="500px" height="300px"></div>

<div align="center"><img src="img/val_0.001.png" alt="Logo" width="500px" height="300px"></div>

<div align="center"><img src="img/val_0.01.png" alt="Logo" width="500px" height="300px"></div>


Therefore, both of **tanh** activation function and **0.001** learning rate was chosen for the final model. As we can see in the first image, the final accuracy score for the training images is `100%` and `99.9%` for the validation images. In the second picture, the training loss was `3.55 *10-3` and `0.04` for validation images.


<div align="center"><img src="img/final_model_acc.png" alt="Logo" width="500px" height="300px"></div>

<div align="center"><img src="img/final_model_val.png" alt="Logo" width="500px" height="300px"></div>

<br><br>

[//]: # (&#40;____________________________________ CONCLUSION____________________________________&#41;)

<img src="https://media4.giphy.com/media/MbMUCH4MUffka1ZFeT/giphy.gif?cid=790b7611040baf4e7332c491694685e3367d8fe931cd7a69&rid=giphy.gif&ct=s" alt="Smiley face" width="80" height="60" align="left">

## Conclusion:
<hr style="height:1.5px;border-width:10;color:blue;background-color:black">

Different model hyperparameters were tested and in general, most of the models prefer well in the range of **10** epochs. For the learning rate, `0.001` give us the highest score and then `0.0001` and finally `0.1`. As for the activation function, there is no bad one, `tanh` gives a better result with a small learning rate like **0.0001** and **0.001** and for a big learning rate like **0.1**, `relu` gives a better result.

Our best model test score is `99.7%` with a loss equal to `0.0371`.

