---
layout: post
title: Reflection on Creating my first fast.AI model
date: 2019-05-26 20:51 -0400
---

I've started to take the Practical Deep Learning for Coders course by Jeremy Howard and Rachel Thomas. The first lesson involved the building of a model to classify and differentiate between different dog and cat breeds based off the [Oxford IIIT dataset](https://www.robots.ox.ac.uk/~vgg/data/pets/). Following along, resulted in similar results with low error thresholds.

I determined to follow along with what Howard stated to do at the end of the video, to find his student Francisco's article on how to scrape Google Images and build a classifier.

Nevertheless, it did not go as well as that of the prepared Oxford IIIT classifier.

I was stuck on what thing to classify originally; Since the lesson classified animal breeds, that felt too easy and very much a re-do. I decided that I would classify chairs based off the 8 different types as shown in [this image](https://www.pinterest.com/pin/596515913117819854/) (Tub, Lawson, Wingback, Slipper, Bergere, Modern Wingback, Club, Occasional).

The first thing I did was follow the instructions in [this repo](https://github.com/fpingham/google-images-dataset/blob/master/download_images.ipynb) by fpingham in order to obtain the images for each respective chairtype (Certain methods of data retrieval can violate a given company's terms of service and lead to lawsuits).

That is, I searched for the type in Google Images, scrolled down until I could not scroll anymore, opened the javascript console (right-click, inspect element, and click console), and ran the following code:

```javascript
urls = Array.from(document.querySelectorAll('.rg_di .rg_meta')).map(el=>JSON.parse(el.textContent).ou);
window.open('data:text/csv;charset=utf-8,' + escape(urls.join('\n')));
```

The first line grabs the urls from the google image page and parses them into a JSON object. The second line creates a data file with these urls and attempts to open it. Given that the default browser protocol is to block popups (this is a good protocol), you'll probably see a yellow popup notification. You can allow it, since it's your data file.

I did this 8 times, once for each respective chair type.

For this course, I am using colaboratory, which is awesome because it means that I can run jupyter-like notebooks in the cloud with a GPU runtime, all for free.

Using colaboratory instead of your standard jupyter notebook introduces a few headaches in terms of importing data into it, but it's nothing we can fix. [This article](https://towardsdatascience.com/3-ways-to-load-csv-files-into-colab-7c14fcbdcb92) explains the 3 principle ways to pass data into colaboratory.

The way I used was `uploaded = files.upload()` a.k.a the local file upload method. I used this function in my colab notebook:

```python
from google.colab import files
def upload(path):
    uploaded = files.upload()
    with open(path,'wb') as fp:
        fp.write(uploaded[list(uploaded.keys())[0]])
```

Running this function in colab (<kbd>Shift + Enter</kbd>), will open file explorer for each respective file, to upload it. colaboratory is notable in that since it's free, it only keeps your uploaded file for up to 12 hours.

Having successfully imported the url data into colaboratory, I defined the chair types, attempted to download the images, and proceeded to create a DataBunch from the validated images.

![Chair examples](https://cldup.com/HHa8znhODL-3000x3000.png)

I then ran resnet on the data, created a `ClassificationInterpretation`, and plotted the top losses (the most mistaken).

Here is a summary of the results.

|            | resnet34 | resnet34 w/ loss minimalization | resnet50 | resnet50 w/ loss minimalization |
|------------|----------|---------------------------------|----------|---------------------------------|
| Error Rate | 50%      | 49%                             | 46.5%    | 45.5%                           |

That's a pretty horrible error rate, regardless of the CNN and additional minimization we do. Our best case of predicting a chair into one of these 8 types is a *54.5% chance*.

I pin the culprit on a multitude of factors, most notably...

## My categories sucked

The classes I defined were **tub**, **lawson**, **wingback**, **bergere**, **modern wingback**, **club**, and **occasional**.

The confusion matrix for resnet34 showed that tub and lawson were the most confused, but upon using a larger normalized size for the images (299 vs 224), and 50 layers over 34 layers, this is minimalized to a trivial number (3 / 40). The most confused as spitted out by `interp.most_confused(min_val=2)` is then

```python
[('modern_wingback', 'wingback', 6),
 ('occasional', 'tub', 6),
 ('wingback', 'bergere', 6),
 ('wingback', 'modern_wingback', 6),
 ('wingback', 'occasional', 6),
 ('club', 'occasional', 5),
 ('occasional', 'lawson', 5),
 ('occasional', 'slipper', 5),
 ('club', 'tub', 4),
 ('slipper', 'bergere', 4),
 ('wingback', 'slipper', 4),
 ('club', 'lawson', 3),
 ('modern_wingback', 'club', 3),
 ('modern_wingback', 'lawson', 3),
 ('modern_wingback', 'slipper', 3),
 ('slipper', 'club', 3),
 ('slipper', 'modern_wingback', 3),
 ('slipper', 'occasional', 3),
 ('slipper', 'wingback', 3),
 ('tub', 'club', 3),
 ('tub', 'lawson', 3),
 ('tub', 'slipper', 3),
 ('bergere', 'lawson', 2),
 ('bergere', 'wingback', 2),
 ('club', 'wingback', 2),
 ('lawson', 'club', 2),
 ('lawson', 'modern_wingback', 2),
 ('lawson', 'occasional', 2),
 ('lawson', 'slipper', 2),
 ('lawson', 'tub', 2),
 ('modern_wingback', 'occasional', 2),
 ('occasional', 'modern_wingback', 2),
 ('wingback', 'lawson', 2)]
```

Modern wingback and wingback were confused 6 times, which given the data retrieval method, makes sense since a google image search for the general category "wingback" probably yielded both wingback and modern wingback chairs.

The interesting thing as yielded from `interp.most_confused` though is that occasional is confused with five categories relatively high: tub, wingback, club, lawson, and slipper.

Given that I lifted the categories from an image, without actually looking whether the category definitions made sense, looking at [this link](https://www.thespruce.com/occasional-chairs-1391722) makes my model look suddenly so much more bearable.

> An occasional chair or accent chair may belong to any style, shape, color or form. The upholstery on the chair may be patterned, solid, or a combination. It can be textured or smooth, covering a frame completely, or leaving the frame uncovered.

## I did no data sanitization

The images were directly imported from Google Images. This meant that some of the images that showed up were not exactly correct depictions of the respective chair type. This was a pretty significant problem with lawson chair type especially, with google images showing Lawson the place, Lawson the person, sofas, and various other types of furniture.

<figure>
    <img src="https://cldup.com/iZXzPU8Vl2-3000x3000.png" alt="lawson chair google results"/>
    <figcaption>Clearly at least a fourth of these is not a picture of even a chair. (No, James Lawson is the chair of a university, not an actual *physical* chair)</figcaption>
</figure>

## Overall

Overall, I think a 55% chance of getting a chair type right is pretty good, given the aribtrarily vague definitions of my categories, and the lack of data sanitization.