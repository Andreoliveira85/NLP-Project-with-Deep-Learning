# NLP-Project-with-Deep-Learning: Construction of a Translator machine

## Project description:

According to the Google paper [*Attention is all you need*](https://arxiv.org/abs/1706.03762), you only need layers of Attention to make a Deep Learning model understand the complexity of a sentence. We will try to implement this type of model for our translator. 

## Project description 

 

Our data can be found on this link: https://go.aws/38ECHUB

### Preprocessing 

The whole purpose of your preprocessing is to express your (French) entry sentence in a sequence of clues.

i.e. :

* je suis malade---> `[123, 21, 34, 0, 0, 0, 0, 0]`

This gives a *shape* -> `(batch_size, max_len_of_a_sentence)`.

The clues correspond to a number that you will have to assign for each word token. 

The zeros correspond to what are called [*padded_sequences*](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/sequence/pad_sequences) which allow all word sequences to have the same length (mandatory for your algorithm). 

This time, we won't have to *one hot encoder* your target variable. We  will simply be able to create a vector similar to your input sentence. 

i.e. : 

* I am sick ---> `[43, 2, 42, 0, 0]`

WARNING, we  will however need to add a step in our preprocessing. For each sentence we will need to add a token `<start>` & `<end>` to indicate the beginning and end of a sentence. We can do this via `Spacy`.

We will use : 

* `Pandas` or `Numpy` for reading the text file.
* `Spacy` for Tokenization 
* `Tensorflow` for [padded_sequence](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/sequence/pad_sequences) 

### Modeling 

For modeling, we will need to set up layers of attention. We will need to: 

* Create an `Encoder` class that inherits from `tf.keras.Model`.
* Create a Bahdanau Attention Layer that will be a class that inherits `tf.keras.layers.Layer`
* Finally create a `Decoder` class that inherits from `tf.keras.Model`.


We will need to create your own cost function as well as our own training loop. 


### Tips 

We will not take the whole dataset at the beginning for our experiments, we just take 5000 or even 3000 sentences. This will allow us to iterate faster and avoid bugs simply related to your need for computing power. 

Also, we acknowledge the inspiration from the [Neural Machine Translation with Attention] tutorial (https://www.tensorflow.org/tutorials/text/nmt_with_attention) from TensorFlow. 

## Code/resources used:**
**Python version:** 3.7
**Libraries/packages used:** keras, tensorflow, numpy
