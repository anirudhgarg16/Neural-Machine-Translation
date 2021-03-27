# Neural-Machine-Translation

Neural Machine Translation (NMT) is the task of using articial neural network models for translation from one
language to the other. The NMT model generally consists of an encoder that encodes a source sentence into a fixed-length vector from which
a decoder generates a translation. This problem can be thought as a prediction problem, where given a sequence of words in source language as input,
task is to predict the output sequence of words in target language.

The dataset comes from http://www.manythings.org/anki/, which consists of delimited bilingual sentence pairs in
different files based on the source and target language of your choice. For this project, I have used French - English 
language pairs for building the model.



## Steps Followed

* ### Cleaning the Data

   *  Download the data as zip file and extract it to corresponding txt file. Read this txt file and prepare the list of pairs of
      language phrases.

   * Now, we need to clean these pairs. For cleaning the text, some of the operations for cleaning are:
     *  Remove the non printable charaters, if any.
     *  Remove punctuations and non-alphabetic charaters.
     *  Convert to lowercase.

* ### Split and Prepare the Data for Training the Model
   
   *  Create separate tokenizer for both source language and target language.
   
   *  After creating the tokenizer, encode and pad the input (source language) and output(target language)
      sequences w.r.t. their individual tokenizers and maximum sequence lengths.
      
   *  Here, in this problem we will essentially be predicting the words in target language, therefore output seuences will need
      to be converted in one hot encoding.
      
   *  Split the data in train and test.


* ### Define and Train the LSTM (Long Short-Term Memory) based Model
 
   *  Define the Sequential Model consisting mainly of two parts - Encoder and Decoder.
   
   *  In Encoder, the input sequence shall be passed through an Embedding layer (to train the word embeddings for source
      language) and then the output from the Embedding layer may be passed through one or more RNN/LSTM layers.  
      
   *  Now, to connect this Encoder to Decoder (yet to be defined), we can use RepeatVector layer. (This is because the shape
      of the output by Encoder is not same as expected shape of Input by Decoder)
      
   *  Now, stack up the Decoder, wherein you may add one or more RNN/LSTM layers and finally the output TimeDistributed
      Dense layer to get output separately by timesteps.
      
   *  The model can now be trained on the Training Data. 
 
 
* ### Evaluate the Model

   *  The model can be evaluated using the BLEU Score from the NLTK Library.



