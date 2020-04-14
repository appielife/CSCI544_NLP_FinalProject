# CSCI544_NLP_FinalProject
This repository is implementation of our final project titled 'Intelligent Question Generation from text using sequence to sequence model'.
This project is implemented by Arpit Parwal and Tridha Choudhary

<h3>Model</h3>
(Xinya Du et al., 2017) original model was written in Lua-torch and uses OpenNMT which is a fantastic neural machine translation toolkit.
As the NLP community has shifted to using Tensorflow and PyTorch in the recent times, we implemented the model
in TensorFLow.
<br>We choose word embedding of 300 dimensions and use the <b>glove.840B.300d pre-trained embeddings</b> (Pennington et al., 2014)
for initialization.

<h3>Dataset</h3>
The dataset used for the our experiments, is the Stanford Question Answering Dataset (SQuAD) (Rajpurkar et al., 2016). This is a relatively
large dataset and is composed of questions posed by crowd workers.

<h3> Version need to be exact in order for the program to run </h3>
python 2.7
numpy
Tensorflow 1.4


<h2>IMPORTANT INSTRCTIONS TO RUN THE PROJECT </h2>

<I>
<br>
When logged in to GCP <br>
Go to Computer Engine --> VM Instances from the left menu
You will see and instance running with the name instance-1, if not you can start the instance.
Click on SSH under connect column and it will connect you to the instance directly. 

<h4>Enter into the directory</h4>
cd code 

<h4> Create a virtual Env for Tensorflow</h4>
virtualenv --system-site-packages -p python2.7 ./venv
source ./venv/bin/activate  # sh, bash, ksh, or zsh

Ref. https://www.tensorflow.org/install/pip?lang=python2

<h4> Run the model </h4>
bash run.sh pred squad basic_params 0 

IMP: Due to large dataset size the file take >5 hours to complete the entire dataset.
You can stop the process after 15 minutes and can see the partially generated pred.txt.

This will generate a file in result folder with the name pred.txt 

You can find our result in result_final folder

Feel free to contact +1(770) 568-7578 or aparwal@usc.edu for any clarification. 



<h2> TRAINING INSTRUCTION (in case you want to see how we achieved this result and BLEU values during compution) </h2>

<h4>Download & process GloVe</h4>
// NOT Required as data already exist //
wget http://nlp.stanford.edu/data/glove.840B.300d.zip -P data/  <br>
unzip data/glove.840B.300d.zip -d data/  <br>
python process_embedding.py

<h4>Train model</h4>
bash run.sh train squad basic_params 10 <br>

<h4>Test model</h4>
bash run.sh pred squad basic_params 0 <br>




