# face-of-fonts
Typeface recommendation project using deep learning with dataset taken from corporate branding guides. Won the first prize on the [Tsinghua's brain inspired competition](https://istd.sutd.edu.sg/news-events/event/news/first-place-1st-annual-tsing-hua-brain-inspired-computing-competition/)

## Inspiration
Each typography has its own meaning. Therefore, when a company wants to design its own fonts, they will have to use the font that can stand for their company culture. Bearing this in mind, we explore the relationship between a company's culture and the typography they use.

We use [online scraping](https://github.com/Emrys-Hong/face-of-fonts/tree/master/data_scraping_scripts) to scrape the mission and vision statement of each company, and the font they use as their official font from their official website, as well as LinkedIn.

During scraping, one interesting finding is that companies related to technology prefer sans-serif for their futuristic feeling while universities prefer serif (like Garamond) for their seriousness. if you are interested in the intuition behind click [here](https://github.com/Emrys-Hong/face-of-fonts/blob/master/presentation_material/Faces_of_Fonts_Paper.pdf)

## Solution
Here we collected a dataset of the 9 most common fonts used by a big company. With a training set of total 2300. we wish to predict what font is suitable for the company based on their vision and mission statement.

We used [CNN architecture for text classification](https://arxiv.org/pdf/1408.5882.pdf) published by Yoon Kim as a base architecture with a bit of [moderation](https://datawarrior.wordpress.com/2016/10/12/short-text-categorization-using-deep-neural-networks-and-word-embedding-models/) on the architecture. Getting a prediction of 45.5%. We are confident that there are more things to be explored between a company's culture and font!

## Based line
The baseline for this project using the simple [SVM](https://www.csie.ntu.edu.tw/~cjlin/liblinear/) gives a result of about 22%.

## Downloads
You will need 'GoogleNews-vectors-negative300.bin.gz' or [GloVe](https://nlp.stanford.edu/projects/glove/) for the word embeddings. We did not include it in this repository.

## Run this project
1. download the word vectors, we used 300d GLoVe vector.
1. install packages using requirements.
1. run ```python model/classify.py``` to test the accuracy

Result: It trains about 4 mins on a normal PC with only CPU. You should get an accuracy of around 46%.

## To make things even cooler
We can turn each font to its corresponding vector, using a completely new idea -- Font2vec from ["fontjoy"](https://github.com/Jack000/fontjoy) for thousands of Google fonts. And then after getting your predicted result in each portion of the font, you can see what the composed font is by adding all of your font vector vectors together. This enables you to get predictions not limited to 9 fonts but to all 900 google fonts. Check here for a quick idea of [font2vec](https://fontjoy.com/projector/)
![fontjoy](https://github.com/Emrys-Hong/face-of-fonts/blob/master/fontjoy.png)

To do this run ```python inference/GUI.py```
the final prediction looks something like this:
![demo](https://github.com/Emrys-Hong/face-of-fonts/blob/master/demo.png)

Credits to [TensorFlow implementation of Text Classifier](https://github.com/cahya-wirawan/cnn-text-classification-tf)
