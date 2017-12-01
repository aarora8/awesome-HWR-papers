# awesome-HWR-papers
Handwritten Word recognition papers, includs HMM-GMM, HMM-DNN, RNN-CTC, MDLSTM, CNN-RNN, sequence discriminative training

Handwriting recognition is a task of interpreting handwritten inputs from sources such as image of text written on a paper, touch screen, electronic whiteboard or other devices. This task is subdivided among two categories offline recognition and online recognition. Offline recognition involves recognition of handwritten images, whereas online recognition also have addition time information of each stroke example pen trajectory and up/ pen down information. Online handwritten recognition is relatively an easier task as in addition to image features, it also have temporal feature from pen trajectory. This repo covers papers dicussing different optical and language modeling approaches for offline cursive recognition of handwritten text. The papers are mostly focused around IAM and Rimes dataset.

# IAM

IAM dataset is an english offline handwriting database. It contains text line images, text paragraph images and word images.  The images were scanned at a resolution of 300dpi and saved as PNG images with 256 gray levels. There are about 115k word images, 13k line images and 1.5k paragraph text images in the dataset. In the Large Writer Independent Text Line Recognition Task, it have 6161 text lines, 283 writers in training and 1861 lines and 128 writers in testing. There are 79 unique characters in test and train set. The line images of the training set have an average width of 1,781 pixels with 152 pixels standard deviation and an average height of 124 pixels with 34 pixels standard deviation. Each line image have around 8 words and height of line images varies between 70-100 pixels. Its sentences are taken from LOB corpus. 
 
# official splits
testset.txt - lines: 1861 writers: 128\
trainset.txt - lines: 6161 writers: 283\
validationset1.txt - lines: 900 writers: 46\
validationset2.txt - lines: 940 writers: 43\
total - lines: 9862 writers: 500

# aachen
testset.txt - lines: 2915\
trainset.txt - lines: 6161\
validationset1.txt - lines: 966\
total - lines: 10042

SAT triphone gmm baseline: 70% WER\
chain recipe: 39% WER \
when I use a lexicon which only includes all the training 
transcriptions (there are ~1800 OOVs while the total number 
of unique words in the test set is 3600).

after adding all the test words to the language model  as 1-grams: WER 23%.\

FSF: I used 5 for this since the best gmm systems had 6-7 hmm states for each phone (which is ~2x regular size).\
Number of leaves (i.e. pdf ids): I used 300 which worked well for gmm setup\
Training options such as learning rate and frames per iteration and num jobs initial/final. I used 1000,000 frames per iter which leads to 4 training egs archives and 26 iterations (for 4 epochs). \
chunk width: I used "340,300,200,100" because I thought the input alignments might not be very reliable so it might be better to have longer chunks so that the model has more freedom to re-learn the alignments.\
Other chain options such as regularization configs, shrinkage, ...
