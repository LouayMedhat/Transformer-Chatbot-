In the code we prepare the model to train we put the hyperparameters 
MAX_LENGTH, MAX_SAMPLES,  
BATCH_SIZE, BUFFER_SIZE, NUM_LAYERS, NUM_LAYERS, NUM_HEADS, UNITS, 
DROPOUT and EPOCHS To keep this model small and relatively fast, the values for 
num_layers, d_model, and units have been reduced Data Preprocessing: 
 The preprocess_sentence function preprocesses a sentence by converting it 
to lowercase, removing extra spaces, replacing contractions with their 
expanded forms, and removing non-alphabetic characters. 
 The load_conversations function reads the movie lines and conversations 
from the Cornell Movie Dialogs dataset files and preprocesses the input 
and output sentences. 
The questions and answers variables store the preprocessed conversation 
data. 
The tokenizer is built from the corpus of questions and answers using the 
SubwordTextEncoder from TensorFlow Datasets (tfds). 
Tokenization and Filtering: 
 The START_TOKEN and END_TOKEN are added to the tokenizer's 
vocabulary to indicate the start and end of a sentence. 
The VOCAB_SIZE is the total vocabulary size after tokenization. 
The tokenize_and_filter function tokenizes the input and output 
sentences, adds start and end tokens, and filters out sentences longer than 
MAX_LENGTH. 
 The filtered tokenized inputs and outputs are padded to have a fixed 
length using tf.keras.preprocessing.sequence.pad_sequences. 
Ai Platefom  
Dataset Creation: 
 The dataset is created from the tokenized inputs and outputs, split into 
input and decoder inputs, and output sequences. 
 The dataset is cached, shuffled, batched, and prefetched for optimized 
training. 
Attention Mechanism: 
 The scaled_dot_product_attention function performs scaled dot-product 
attention given query, key, value, and an optional mask. 
The MultiHeadAttentionLayer class represents a single layer of the multi
head attention mechanism. The layer splits the input into multiple heads, 
applies scaled dot-product attention, and concatenates the outputs.
