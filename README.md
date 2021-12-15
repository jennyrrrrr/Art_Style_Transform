## Abstract 

The greatest painters left amazing art works to us, and we are still admiring their art and style until today. It would 
amazing if we can replicate the same style from them. And you can easily turn any photography you like into the same 
Monet or Van Gogh yourself. 

This Project is a learning and experimentation of the Cycle GAN from the paper <em>Unpaired Image-to-Image Translation 
using Cycle-Consistent Adversarial Networks</em> . In this project I trained a Clycle GAN model by following the methods 
described in the original paper. The data I'm using to tain includes photot of real life views, Monet's paintings, Van 
Gogh's paintings(sketches). The example training images were very close to real life looking paintings, so i also trained a
network using sketches from Van Gogh's paintings. 

![input](images/paper_res.png)

<figcaption align = "center"> Cycle GAN result image from <em>Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial 
Networks</em> </figcaption>


## Problem statement 

In training image to a different style, I would be much easier to used paired photo and paintings for training. 
But in most cases, we don't have such ability to paired data. The problem statement is how can we generate image with 
certain styles without having a good amout of paired data. For example, if we want to transform a real life photography to a Van Gogh styled painting, we will not be able to get 
a real life photography matching Van Gogh styled painting.

<p align="middle">
    <img src="images/problem.png" alt="Screenshot of the app" height="400" />
</p>
<figcaption align = "center"> Example paired/unpaired image from <em>Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial 
Networks</em> </figcaption>

## Related work 

### Paper

Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks
https://arxiv.org/pdf/1703.10593.pdf

### Data

1. Photography

https://www.kaggle.com/c/gan-getting-started

2. Monet Paintings

https://www.kaggle.com/c/gan-getting-started

3. Van Gogh Paintings

https://www.kaggle.com/ipythonx/van-gogh-paintings

<p align="middle">
<img src="./images/photo.png" alt="Screenshot of the app" height="400" />
<img src="./images/monet.png" alt="Screenshot of the app" height="400" />
<img src="./images/sketch.png" alt="Screenshot of the app" height="400" />
</p>

### Package 
Unpaired image-to-image translation

https://github.com/tmabraham/UPIT

### Kaggle
I’m Something of a Painter Myself

https://www.kaggle.com/c/gan-getting-started

https://www.kaggle.com/dimitreoliveira/improving-cyclegan-monet-paintings

## Methodology

To generate images in certain style, we are transforming data from domain X (photos) to domain Y (styled paintings). 

First, we need a distriminator to jude if the generated image belongs to domain Y. 

But using only the discriminator may cause problems like generating images that look like it's a image in domain Y, 
but the generated image may turned out to have nothing in relation with the input image. 

So to avid problem like this, another generater is needed to transform the image from domain y back to image in 
domain X, we need to make the regenerated input image to be as close as to the original input image. 

So we also need another generator and discriminator to use the generated painting to regenerate image back in domain X. 

And as I noticed that the dataset prsented in the original paper are using data/images that are close to the realistic 
style. Thus I also tried training on a more dramatic and different style of data, I also tried the penciel skeches from Van Gogh's 
paintings dataset.

<p align="middle">
    <img src="images/model3.png" alt="Screenshot of the app" height="400" />
</p>
<figcaption align = "center"> Graphic representation of the Model. </figcaption>

### Discriminator

<p align="middle">
    <img src="images/discriminator.png" alt="Screenshot of the app" height="400" />
</p>

After the last layer, a convolution is applied to map to
a 1-dimensional output, followed by a Sigmoid function.

### Generator

Here is the ResNet-block-based architecture of the generator. 
With 3 convolutional layers of encoder, 6 layers of residual block, and 3 convolutional layers of decoder. 

<p align="middle">
    <img src="images/generator.png" alt="Screenshot of the app" height="400" />
</p>

## Experiments/evaluation 

- how are you evaluating your results

## Examples

Some example image and paintings generated with the trained model. 

### Monet:

photo -> painting
<p align="middle">
    <img src="images/monet_res.png" alt="Screenshot of the app" height="400" />
</p>

### Van Gogh sketches:

painting -> photo
<p align="middle">
    <img src="images/my_res.png" alt="Screenshot of the app" height="400" />
</p>
painting -> photo

## Results

The model I implemented and trained is successful in making Monet styled painting and Van Gogh styled sketches from 
real life photography.

As a result, it takes way to long and GPU consuming a train the GAN model , and after training 120 epoches with the Monet paintings data set and 13 epoches with Van Gogh's sheckes, my chrome/computer
finally crashed.

I would say it is pretty successful in generating the paintings and photos to the styles I want.


## Video

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg)](https://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_HERE)



@Misc{UPIT,
    author =       {Tanishq Mathew Abraham},
    title =        {UPIT - A fastai/PyTorch package for unpaired image-to-image translation.},
    howpublished = {Github},
    year =         {2021},
    url =          {https://github.com/tmabraham/UPIT}
}
