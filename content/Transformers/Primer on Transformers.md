---
title: "Transformers:Self Attention Mechanism"
---

The **transformer** is one of the most popular state-of-the-art deep learning architectures that is mostly used for natural language processing (NLP) tasks. Ever since the advent of the transformer, it has replaced the recurrent neural network (RNN) and long short-term memory (LSTM) for various tasks. Several new NLP models, such as BERT, GPT, and T5, are based on the transformer architecture.

RNN and LSTM networks are widely used in sequential tasks such as next word prediction, machine translation, text generation, and more. However, one of the major challenges with the recurrent model is capturing the long-term dependency.

To overcome this limitation of RNNs, a new architecture called Transformer was introduced in the paper “Attention Is All You Need.” The transformer is currently the state-of-the-art model

The transformer model is based entirely on the attention mechanism and completely gets rid of recurrence. The transformer uses a special type of attention mechanism called self-attention.

### How does the transformer work ?
Let's understand how the transformer works with a language translation task. The transformer consists of an encoder-decoder architecture. We feed the input sentence (source sentence) to the encoder. The encoder learns the representation of the input sentence and sends the representation to the decoder. The decoder receives the representation learned by the encoder as an input and generates the output sentence (target sentence).
\
Suppose we need to convert a sentence from English to French. We feed the English sentence as input to the encoder. The encoder learns the representation of the given English sentence and feeds the representation to the decoder. The decoder takes the encoder's representation as input and generates the French sentence as output
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 862.4798583984375 60.26307078613121" width="862.4798583984375" height="60.26307078613121">
  <!-- svg-source:excalidraw -->
  
  <defs>
    <style class="style-fonts">
      @font-face {
        font-family: "Virgil";
        src: url("https://excalidraw.com/Virgil.woff2");
      }
      @font-face {
        font-family: "Cascadia";
        src: url("https://excalidraw.com/Cascadia.woff2");
      }
      @font-face {
        font-family: "Assistant";
        src: url("https://excalidraw.com/Assistant-Regular.woff2");
      }
    </style>
    
  </defs>
  <rect x="0" y="0" width="862.4798583984375" height="60.26307078613121" fill="#ffffff"></rect><g stroke-linecap="round" transform="translate(10 11.103097829757019) rotate(0 61.497704008953804 19.579986478187095)"><path d="M9.79 0 C46 -1.83, 82.42 -0.6, 113.21 0 M9.79 0 C42.46 1.14, 72.54 -0.27, 113.21 0 M113.21 0 C118.88 -0.74, 123.16 2.19, 123 9.79 M113.21 0 C117.9 -2.14, 123.04 3.72, 123 9.79 M123 9.79 C122.02 12.76, 122.02 16.34, 123 29.37 M123 9.79 C123.72 16.92, 123.76 24.55, 123 29.37 M123 29.37 C124.93 37.14, 120.3 39.59, 113.21 39.16 M123 29.37 C122.6 37.75, 120.58 40.54, 113.21 39.16 M113.21 39.16 C82.87 37.03, 48.43 36.97, 9.79 39.16 M113.21 39.16 C78.13 38.59, 45.38 38.41, 9.79 39.16 M9.79 39.16 C3.82 39.82, -0.28 37.29, 0 29.37 M9.79 39.16 C1.28 37.96, -1.78 34.01, 0 29.37 M0 29.37 C-1.54 23.4, -1.81 19.44, 0 9.79 M0 29.37 C0.78 24.17, -0.4 20.54, 0 9.79 M0 9.79 C-0.39 4.65, 4.46 -1.27, 9.79 0 M0 9.79 C1.46 1.76, 1 0.63, 9.79 0" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(39.49171493424683 23.78872287196276) rotate(0 32.00598907470703 6.894361435981381)"><text x="32.00598907470703" y="9.663136988671486" font-family="Virgil, Segoe UI Emoji" font-size="11.030978297570188px" fill="#1971c2" text-anchor="middle" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">I am Good </text></g><g stroke-linecap="round"><g transform="translate(134.65005476254316 30.155853673738136) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M0.37 -0.53 C11.79 -0.48, 56.94 -0.65, 68.5 -0.4 M-0.89 1.8 C10.33 2.06, 55.61 1.26, 67.32 0.79" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(134.65005476254316 30.155853673738136) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M44.06 9.96 C50.19 6.4, 56.95 5.65, 67.32 0.79 M44.06 9.96 C51.65 6.78, 61.55 3.55, 67.32 0.79" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(134.65005476254316 30.155853673738136) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M43.6 -7.13 C49.77 -5.58, 56.67 -1.21, 67.32 0.79 M43.6 -7.13 C51.26 -4.19, 61.32 -1.28, 67.32 0.79" stroke="#1971c2" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round" transform="translate(204.14521803723528 10) rotate(0 59.843057264318304 19.304212020747826)"><path d="M9.65 0 C30.26 -2.51, 50.3 0.45, 110.03 0 M9.65 0 C34.49 1.41, 61.05 0.05, 110.03 0 M110.03 0 C114.78 0.86, 121.5 1.91, 119.69 9.65 M110.03 0 C117.89 -1.17, 120.53 1, 119.69 9.65 M119.69 9.65 C120.57 13.28, 119.61 20.66, 119.69 28.96 M119.69 9.65 C119.69 16.56, 119.3 22.17, 119.69 28.96 M119.69 28.96 C120.86 36.51, 115.66 39.16, 110.03 38.61 M119.69 28.96 C117.52 37.04, 118.08 38.69, 110.03 38.61 M110.03 38.61 C72.1 38.21, 39.91 39.56, 9.65 38.61 M110.03 38.61 C76.2 37.69, 42.91 39.23, 9.65 38.61 M9.65 38.61 C3.06 38.82, 1.13 34.94, 0 28.96 M9.65 38.61 C4.73 37.89, -1.72 37.3, 0 28.96 M0 28.96 C1.03 22.32, 1.17 17.89, 0 9.65 M0 28.96 C0.34 24.52, -0.06 20.05, 0 9.65 M0 9.65 C1.27 4.9, 5.21 -1.2, 9.65 0 M0 9.65 C-1.06 3.33, 1.55 1.03, 9.65 0" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(238.06702147408942 21.582527212448724) rotate(0 21.470233212792607 7.170135893420621)"><text x="0" y="10.049662468218342" font-family="Virgil, Segoe UI Emoji" font-size="11.472217429472995px" fill="#1971c2" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">Encoder</text></g><g stroke-linecap="round"><g transform="translate(326.68206048857724 27.831859667472145) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M0.38 -0.32 C11.81 -0.46, 57.8 -0.37, 69.26 -0.31 M-0.87 -1.53 C10.36 -1.56, 56.92 0.48, 68.47 0.94" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(326.68206048857724 27.831859667472145) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M44.65 8.51 C52.6 6.25, 60.72 3.3, 68.47 0.94 M44.65 8.51 C52.36 6.81, 57.46 3.88, 68.47 0.94" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(326.68206048857724 27.831859667472145) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M45.36 -8.58 C53.13 -4.73, 60.99 -1.57, 68.47 0.94 M45.36 -8.58 C52.7 -5.45, 57.6 -3.55, 68.47 0.94" stroke="#1971c2" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round" transform="translate(397.4631127021529 12.206195659514037) rotate(0 59.84305726431825 18.201114190990808)"><path d="M9.1 0 C29.69 1.1, 50.88 1.01, 110.59 0 M9.1 0 C46.23 0.55, 82.61 -0.83, 110.59 0 M110.59 0 C117.61 0.39, 121.43 2.2, 119.69 9.1 M110.59 0 C118.68 -0.69, 118.87 2.21, 119.69 9.1 M119.69 9.1 C119.96 17.24, 118.84 22.42, 119.69 27.3 M119.69 9.1 C119.15 13.08, 119.62 16.51, 119.69 27.3 M119.69 27.3 C119.24 33.76, 117.45 37.32, 110.59 36.4 M119.69 27.3 C117.56 33.81, 118 36.33, 110.59 36.4 M110.59 36.4 C83.48 34.85, 53.95 34.99, 9.1 36.4 M110.59 36.4 C87.22 37.57, 65 36.97, 9.1 36.4 M9.1 36.4 C2.18 38.37, 0.17 35.35, 0 27.3 M9.1 36.4 C3.83 35.64, 1.43 34.99, 0 27.3 M0 27.3 C0.36 21.92, -1.41 16.87, 0 9.1 M0 27.3 C0.67 21.14, 0.23 14.37, 0 9.1 M0 9.1 C-1.15 3.25, 2.45 -0.47, 9.1 0 M0 9.1 C-0.08 5.22, 4.86 -1.99, 9.1 0" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(420.90394158448953 22.134076127327205) rotate(0 40.20235378102876 6.894361435981381)"><text x="0" y="9.663136988671486" font-family="Virgil, Segoe UI Emoji" font-size="11.030978297570188px" fill="#1971c2" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">Representation</text></g><g stroke-linecap="round"><g transform="translate(518.4071359848426 29.96286849434256) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M0.31 -0.9 C11.84 -0.84, 57.33 0.58, 68.97 0.95 M-0.99 1.24 C10.4 0.91, 56.2 -0.52, 68.03 -0.8" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(518.4071359848426 29.96286849434256) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M44.79 8.41 C49.81 5.78, 59.04 5.13, 68.03 -0.8 M44.79 8.41 C53.38 4.45, 62.06 1.44, 68.03 -0.8" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(518.4071359848426 29.96286849434256) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M44.31 -8.69 C49.55 -6.48, 58.92 -2.31, 68.03 -0.8 M44.31 -8.69 C53.1 -6, 61.96 -2.37, 68.03 -0.8" stroke="#1971c2" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round" transform="translate(589.4021350798741 12.757744574392575) rotate(0 59.843057264318304 18.201114190990808)"><path d="M9.1 0 C32.25 -0.5, 50.72 1.91, 110.59 0 M9.1 0 C37.53 1.13, 66.53 0.28, 110.59 0 M110.59 0 C116.06 -0.09, 118.56 4.71, 119.69 9.1 M110.59 0 C115.73 2.3, 119.86 3.93, 119.69 9.1 M119.69 9.1 C118.88 14.48, 119.73 23.12, 119.69 27.3 M119.69 9.1 C119.9 13.56, 118.96 17.46, 119.69 27.3 M119.69 27.3 C118.53 34.29, 117.27 37.51, 110.59 36.4 M119.69 27.3 C117.69 35.49, 118.66 34.28, 110.59 36.4 M110.59 36.4 C87.61 34.9, 66.89 35.57, 9.1 36.4 M110.59 36.4 C70.97 37.44, 29.21 35.82, 9.1 36.4 M9.1 36.4 C1.1 36.15, -0.59 35.18, 0 27.3 M9.1 36.4 C3.36 37.41, 0.18 34.23, 0 27.3 M0 27.3 C0.32 21.3, -1.95 17.49, 0 9.1 M0 27.3 C-0.49 22.39, 0.54 17.04, 0 9.1 M0 9.1 C1.03 2.51, 1.53 0.6, 9.1 0 M0 9.1 C-2.03 0.97, 1.34 0.62, 9.1 0" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(627.7347846639304 23.237173957084224) rotate(0 21.670336330613395 6.894361435981381)"><text x="0" y="9.663136988671486" font-family="Virgil, Segoe UI Emoji" font-size="11.030978297570188px" fill="#1971c2" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">Decoder</text></g><g stroke-linecap="round"><g transform="translate(710.4577159000778 32.51788173384301) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M0.44 0.52 C12.12 0.4, 58.28 -0.41, 69.71 -0.29 M-0.79 -0.25 C10.84 -0.25, 57.65 1.02, 69.17 0.96" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(710.4577159000778 32.51788173384301) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M45.57 9.2 C52.74 8.18, 57.3 4.83, 69.17 0.96 M45.57 9.2 C55.31 6.1, 64.44 3.35, 69.17 0.96" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(710.4577159000778 32.51788173384301) rotate(0 34.47180717990682 0.12572808838336869)"><path d="M45.79 -7.9 C52.97 -4.33, 57.46 -3.09, 69.17 0.96 M45.79 -7.9 C55.3 -4.5, 64.34 -0.75, 69.17 0.96" stroke="#1971c2" stroke-width="2" fill="none"></path></g></g><mask></mask><g transform="translate(787.6839699786983 23.78872287196276) rotate(0 32.39794420986959 6.894361435981381)"><text x="0" y="9.663136988671486" font-family="Virgil, Segoe UI Emoji" font-size="11.030978297570188px" fill="#1971c2" text-anchor="start" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">Je vais bein</text></g></svg>
  Okay, but what's exactly going on here? How does the encoder and decoder in the transformer convert the English sentence (source sentence) to the French sentence (target sentence)? What's going on inside the encoder and decoder?

### Understanding the Encoder of the Transformer

The transformer consists of a stack of 𝑁 number of encoders. The output of one encoder is sent as input to the encoder above it. As shown in the following figure, we have a stack of 𝑁 number of encoders. Each encoder sends its output to the encoder above it. The final encoder returns the representation of the given source sentence as output. We feed the source sentence as input to the encoder and get the representation of the source sentence as output:

			![[Pasted image 20240722102744.png]]


Note that in the transformer paper "Attention Is All You Need_,"_ the authors have used 𝑁=6, meaning that they stacked up six encoders, one above the other. However, we can try out different values of 𝑁. 

Lets Keep N=2 for simplicity

### Encoder's Components

Okay, the question is, how exactly does the encoder work? How is it generating the representation for the given source sentence (input sentence)? To understand this, let's tap into the encoder and see its components. The following figure shows the components of the encoder

![[Pasted image 20240722102922.png]]

From the preceding figure, we can understand that all the encoder blocks are identical. We can also observe that each encoder block consists of two sublayers:

- Multi-head attention
    
- Feedforward network


To understand how multi-head attention works, we first need to understand the self-attention mechanism.

### Self Attention Mechanism

Let's understand the self-attention mechanism with an example. Consider the following sentence:

*A dog ate the food because it was hungry*

In the preceding sentence, the pronoun '_it_' could mean either '_dog_' or '_food_'. By reading the sentence, we can easily understand that the pronoun '_it_' implies the '_dog_' and not '_food_'. But how does our model understand that in the given sentence, the pronoun '_it_' implies the '_dog_' and not '_food_'? Here is where the self-attention mechanism helps us.

### Representation of the words

In the given sentence, ‘_A dog ate the food because it was hungry_’, first our model computes the representation of the word ‘_A_’, next it computes the representation of the word ‘_dog_’, then it computes the representation of the word ‘_ate_’, and so on. While computing the representation of each word, it relates each word to all other words in the sentence to understand more about the word.

### Computing the representation of the words

For instance, while computing the representation of the word '_it_', our model relates the word '_it_' to all the words in the sentence to understand more about the word '_it_'.

As shown in the following figure, in order to compute the representation of the word '_it_', our model relates the word '_it_' to all the words in the sentence. By relating the word '_it_' to all the words in the sentence, our model can understand that the word '_it_' is related to the word '_dog_' and not '_food_'. As we can observe, the line connecting the word '_it_' to '_dog_' is thicker compared to the other lines, which indicates that the word '_it_' is related to the word '_dog_' and not '_food_' in the given sentence:

![[Pasted image 20240722103500.png]]

Okay, but how exactly does this work? Now that we have a basic idea of what the self-attention mechanism is, let's understand more about it in detail.

## What is embedding?

Suppose our input sentence (source sentence) is '_I am good_'. First, we get the embeddings for each word in our sentence. Note that the **embeddings** are just the vector representation of the word and the values of the embeddings will be learned during training.

Let $x_{1}$ ​ be the embedding of the word '_I_', $x_{2}$ ​ be the embedding of the word '_am_', and $x_{3}$ ​ be the embedding of the word '_good_'. Consider the following:

- The embedding of the word '_I_' is $x_{1}$ ​=[1.76,2.22,...,6.66]
- The embedding of the word '_am_' is $x_{2}$ ​=[7.77,0.631,...,5.35]
- The embedding of the word '_good_' is $x_{3}$ ​=[11.44,10.10,...,3.33]

Then, we can represent our input sentence '_I am good_' using the input matrix 𝑋X (embedding matrix or input embedding), as shown here:

> **Note:** The values used in the preceding matrix are arbitrary and used here just to give us a better understanding.

![[Pasted image 20240722104043.png]]

From the preceding input matrix 𝑋, we can understand that the first row of the matrix implies the embedding of the word '_I_', the second row implies the embedding of the word '_am_', and the third row implies the embedding of the word 'good'.
### Dimensions of the embedding matrix 

The dimension of the input matrix $X$ will be 
 $$[sentence\;length * embedding\;dimension]$$
 The number of words in our sentence (sentence length) is 3. Let the embedding dimension be 512; then, our input matrix (input embedding) dimension will be:
 $$
 [3\;*512]
 $$
 Now from the input matrix $X$, we create three new matrices; a **query matrix $Q$,** **key matrix** $K$, and a **value matrix** $V$. 
 These matrices are used in the self attention mechanism
#### How can we create the query, key, and value matrices?
To create these, we introduce three new weight matrices called $W^Q$ , $W^K$, $W^V$
We create the query $Q$, key $K$ and value $V$ by multiplying the matrix $X$ by  $W^Q$ , $W^K$, $W^V$ respectively

> **Note:** The weight matrices $W^Q$ , $W^K$, $W^V$  are randomly initialized, and their optimal values will be learned during training. As we learn the optimal weights, we will obtain more accurate query, key, and value matrices

![[Pasted image 20240722105305.png]]

From the preceding figure, we can understand the following:

- The first row in the query, key, and value matrices— $q_{1}$​ ,$k_{1}$​, and $v_{1}$​—implies the query, key, and value vectors of the word '_I_'.
- The second row in the query, key, and value matrices $q_{2}$​​ , $k_{2}$​, and $v_{2}$​—implies the query, key, and value vectors of the word '_am_'.
- The third row in the query, key, and value matrices— $q_{3}$​ , $k_{3}$​, and $v_{3}$​ —implies the query, key, and value vectors of the word '_good_'.

### Dimensions of the query, key and value matrices

Note that the dimensionality of the query, key, and value vectors is 64. Thus, the dimension of our query, key, and value matrices is:

$$
[sentence\;length\;*64]
$$
Since we have three words in the sentence, the dimensions of the query, key and value matrices are:
$$
[3\;*64]
$$

But still, the ultimate question is, why are we computing this? What is the use of query, key, and value matrices? How is this going to help us? 

### How the self-attention mechanism works
We learned how to compute query, 𝑄 key, 𝐾, and value, 𝑉, matrices and we also learned that they are obtained from the input matrix, 𝑋. Now, let's see how the query, key, and value matrices are used in the self-attention mechanism.

We learned that in order to compute a representation of a word, the self-attention mechanism relates the word to all the words in the given sentence. Consider the sentence '_I am good_'. To compute the representation of the word '_I_', we relate the word '_I'_ to all the words in the sentence, as shown in the following figure:

![[Pasted image 20240722110350.png]]

But why do we need to do this? Understanding how a word is related to all the words in the sentence helps us to learn better representation. Now, let's learn how the self-attention mechanism relates a word to all the words in the sentence using the query, key, and value matrices. The self-attention mechanism includes four steps. Let's take a look at them one by one.

### Step 1 : Calculating the similarity score

The first step in the self-attention mechanism is to compute the dot product between the query matrix $Q$ and the key matrix $K^T$

![[Pasted image 20240722110700.png]]

The following shows the result of the dot product between the query matrix, 𝑄, and the key matrix, $K^T$:

![[Pasted image 20240722110950.png]]
But what is the use of computing the dot product between the query and key matrices? What exactly does $Q\;*K^T$ signify? Let's understand this by looking at the result in detail.

##### The similarity score for 'I'
Let's look into the first row of the $Q\;*K^T$  matrix as shown in the following figure. We can observe that we are computing the dot product between the query vector $q_{1}$, and all the key vectors— $k_{1}(I),\;k_{2}(am),\;k_{3}(good)$. Computing the dot product between two vectors tells us how similar they are.

Therefore, computing the dot product between the query vector  $q_{1}$ and the key vectors $k_{1},k_{2},k_{3}$ tells us how similar the query vector $q_{1}$  is to all the key vectors— $k_{1}(I),\;k_{2}(am),\;k_{3}(good)$, By looking at the first row of the $Q\;K^T$  matrix, we can understand that the word '_I'_ is more related to itself than the words '_am'_ and '_good'_ since the dot product value is higher for $q_{1}*k_{1}$ compared to $q_{1}*k_{2}$ and $q_{1}*k_{3}$:

![[Pasted image 20240722112553.png]]

> **Note:** The values used in the input matrices are arbitrary and used here just to give us a better understanding.

##### The similarity score for 'am'

Now, let's look into the second row of the $Q*K^T$ matrix . As shown in the following figure, we can observe that we are computing the dot product between the query vector, $q_{2}(am)$  and all the key vectors— $k_{1}(I),\;k_{2}(am),\;k_{3}(good)$, and $k_{3}(good)$. This tells us how similar the query vector $q_{2}(am)$  is to the key vectors— $k_{1}(I),\;k_{2}(am),\;k_{3}(good)$ , and $k_{3}(good)$.

By looking at the second row of the $Q*K^T$ matrix, we can understand that the word '_am'_ is more related to itself than the words '_I'_ and '_good_' since the dot product value is higher for $q_{2}*k_{2}$ compared to $q_{2}*k_{1}$ and $q_{2}*k_{3}$​:


![[Pasted image 20240722112715.png]]

##### The similarity score for 'good'

Similarly, let's look into the third row of the $Q*K^T$  matrix. As shown in the following figure, we can observe that we are computing the dot product between the query vector 𝑞3(good)q3​(good) and all the key vectors— $k_{1}(I),\;k_{2}(am),\;k_{3}(good)$. This tells us how similar the query vector 𝑞3(good)q3​(good) is to all the key vectors— $k_{1}(I),\;k_{2}(am),\;k_{3}(good)$.
By looking at the third row of the $Q*K^T$ matrix, we can understand that the word '_good'_ is more related to itself than the words '_I'_ and 'am' in the sentence since the dot product value is higher for $q_{3}*k_{3}$  compared to $q_{3}*k_{1}$  and $q_{3}*k_{2}$:


Thus, we can say that computing the dot product between the query matrix 𝑄, and the key matrix $K^T$, essentially gives us the similarity score, which helps us to understand how similar each word in the sentence is to all other words

### Step 2 : Obtaining the stable gradients

The next step in the self-attention mechanism is to divide the $Q*K^T$  matrix by the square root of the dimension of the key vector. But why do we have to do that? **This is useful in obtaining stable gradients.**

Let $d_{k}$ be the dimension of the key vector. Then we divide $Q*K^T$ by $\sqrt{d_{k}}$  
The dimension of the key vector is 64. So, taking the square root of it, we will obtain 8. Therefore, we divide $Q*K^T$ by 8 as shown in the following figure:

![[Pasted image 20240722114409.png]]

### Step 3 : Normalizing the gradients

By looking at the preceding similarity scores, we can understand that they are in the unnormalized form. So, we normalize them using the softmax function. Applying the softmax function helps in bringing the score to the range of 0 to 1. The sum of the scores equals 1, as shown in the following figure:

We can call the preceding matrix a score matrix. With the help of these scores, we can understand how each word in the sentence is related to all the words in the sentence. For instance, look at the first row in the preceding score matrix. It tells us that the word '_I'_ is related to itself by 90% , to the word '_am'_ by 7%, and to the word '_good'_ by 3%.

### Step 4 : Computing the attention matrix

Okay, what's next? We computed the dot product between the query and key matrices, obtained the scores, and then normalized the scores with the softmax function. Now, the final step in the self-attention mechanism is to compute the attention matrix, 𝑍

The attention matrix contains the attention values for each word in the sentence. We can compute the attention matrix, 𝑍, by multiplying the score matrix by the value matrix $V$ 

$$
Z=softmax\left( \frac{Q*K^T}{\sqrt{ d_{k} }} \right)*V
$$
![[Pasted image 20240722120122.png]]

Say we have the following:

![[Pasted image 20240722120202.png]]

Result of the attention matrix

##### Attention matrix for 'I'
The attention matrix, 𝑍, is computed by taking the sum of the value vectors weighted by the scores. Let's understand this by looking at it row by row. First, let's see how for the first row, $z_{1}$  , the self-attention of the word '_I'_ is computed:

![[Pasted image 20240722120409.png]]


From the preceding figure, we can understand that $z_{1}$  , the self-attention of the word '_I'_ is computed as the sum of the value vectors weighted by the scores. Therefore, the value of  $z_{1}$  will contain 90% of the values from the value vector $v_1(I)$ 7% of the values from the value vector $v_{2}$, and 3% of values from the value vector  $v_{3}$,.

But how is this useful? To answer this question, let's take a little detour to the example sentence we saw earlier, '_A dog ate the food because it was hungry_'. Here, the word '_it'_ indicates '_dog_'. To compute the self-attention of the word '_it_', we follow the same preceding steps. Suppose we have the following:
![[Pasted image 20240722120651.png]]

##### Attention matrix for 'am'
Now, coming back to our example, $z_{2}$ , the self-attention of the word '_am_' is computed as the sum of the value vectors weighted by the scores, as shown in the following figure:

![[Pasted image 20240722120925.png]]

As we can observe from the preceding figure, the value of $z_{2}$​ will contain 2.5% of the values from the value vector $v_{1}$, 95% of the values from the value vector $v_{2}$ and 2.5% of the values from the value vector $v_{3}$.

##### Attention matrix for 'good'
Similarly, $z_{3}$ , the self-attention of the word good is computed as the sum of the value vectors weighted by the scores, as shown in the following figure:
![[Pasted image 20240722121306.png]]
his implies that the value of $z_{3}$ will contain 21% of the values from the value vector $v_{1}(I)$ 3% of the values from the value vector $v_{2}(am)$, and 76% of values from the value vector $v_{3}(good)$.

Therefore, the attention matrix, 𝑍Z, consists of self-attention values of all the words in the sentence and it is computed as follows:
$$
Z=softmax\left( \frac{Q*K^T}{\sqrt{ d_{k} }} \right)*V
$$
### Summary 

To get a better understanding of the self-attention mechanism, the steps involved are summarized as follows:
1. We compute the dot product between the query matrix and the key matrix, $Q*K^T$ , and get the similarity scores.
2. We divide $Q*K^T$ by the square root of the dimension of the key vector $d_{k}$ .
3. We apply the softmax function to normalize the scores and obtain the score matrix $\frac{softmax(QK^T)}{\sqrt{ d_{k} }}$
4. We compute the attention matrix, 𝑍, by multiplying the score matrix by the value matrix 𝑉.

The self-attention mechanism is graphically shown as follows:
![[Pasted image 20240722121733.png]]
The self-attention mechanism is also called **scaled dot product attention**, since here we are computing the dot product (between the query and key vectors) and scaling the values (with $\sqrt{ d_{k} }$).
