## What is AI ?
The term is often used to describe the process of machine being able to autonomusly take decision and perform tasks close to the human intelligence level
### Laungage AI
Langague AI is the subfield of AI which focuses on technologies focused on understanding, processing and generating human laguages.
The term can be intercahanglably used with NLP but the scope expands further where the LLM technologies encompasses things that might not directly be langugage models but that can have significant impact on the field </br>

### History of Langague Models
1. Bag of Words
2. Word2Vec
3. Attention
4. BERT
5. GPT
5. GPT 2 
6. Roberta
and many more including ChatGPT and Gemini

### Model Elobrated Understanding </br>
1. Bag of Words: Contains below steps
   A. Tokenization: Breaks the statements in tokens (E.g. "Cat sat on a mat" corresponding tokens will be ['Cat','sat','on','a','mat']
   B. Create a dictionary from the individual tokens based on the entire document
   C. Represent the original sentence based on the numerical representation depending presence of the word in sentence (1 if the word exists, 0 if not)

**Limitation**
A. Final representation is just a bag of word without any sementaic meaning E.g. "Tiger ate rabbit" and "Rabbit ate tiger" would essentially be the same sentences

2. **Word2Vec**: It is a NN based model that represents tokens in the high multidimensional space in the form of vector. Words having similar meaning or that appear together in similar context usually are closer to each other compared to the ones 
   that have very different meaning or don't appear toghther often
   The way model works is as below
   1. Words are intially embedded and represented in the form of vectors, and the initial values are randomized
   2. Eventually as the training data is passed to the model, the model tries to optimize similar words (with meaning/context) closer to each other
   3. End output is the vector representation of the words in the high dimensional space

**Advantages**
Preserves some degree of semantic meaning

**Limitation**
The end output is a static representation of the words. However, if the same word appears in a very different context tha was not present in the training data the results are not tha accurate </br>
E.g. "I am standing at a bank". Here the word "bank" can have various meanings depending on the context which can't be adjusted for in the static represenation

**3. Encoder Decoder with Attention Mechanism**

Tokenization:
The input sentence is broken down into individual tokens: ['I', 'love', 'India']. These tokens are sequentially represented as:

rust
Copy code
x1 -> 'I'  
x2 -> 'love'  
x3 -> 'India'
Each token is then passed to the encoder one by one. The encoder is an RNN-based neural network that processes these tokens sequentially.

Processing Tokens:
At each time step, the encoder has two inputs:

The current token (e.g., x1 = 'I').
The previous hidden state (e.g., h0 for the initial step).
At time t = 1:

Input token: x1 = "I".
Previous hidden state: h0 = 0 (since it’s the first step).
New hidden state: h1 = F(h0, x1) (calculated using the RNN function F).
At time t = 2:

Input token: x2 = "love".
Previous hidden state: h1.
New hidden state: h2 = F(h1, x2).
This process continues until all tokens are processed, resulting in the final hidden state (h3) for the last token (x3 = 'India').

Final Hidden State:
The final hidden state (h3) is a summary of the input sentence and contains both:

The vector representation of the tokens processed so far.
Information about the sequence order.
Decoder Side
The decoder is also an RNN-based architecture and operates after the encoder has processed the entire input sequence. The timeline of the decoder is independent of the encoder.

Initialization:
At time t = 0, the decoder’s initial hidden state (s0) is set to the encoder’s final hidden state (h3).

Hidden state: s0 = h3.
Input token: y0 (a special start-of-sentence token added by the decoder).
Context vector: c0 = h3 (initialized to the encoder’s final hidden state).
Generating Output:
At each time step, the decoder generates the next token based on:

The previous hidden state.
The previous output token.
The context vector from the attention mechanism.
For example:

scss
Copy code
s1 = DecoderRNN(s0, y0, c0)
y1 = softmax(Linear(s1))
Attention Mechanism
The attention mechanism ensures that the decoder focuses on relevant parts of the input sentence while generating each output token. This solves issues where the encoder’s final hidden state alone may not fully capture long or complex sentences.

Context Vector (c1):
Instead of using just the encoder’s final hidden state (h3), the context vector is computed as a weighted sum of all encoder hidden states (h1, h2, h3):

makefile
Copy code
c1 = α11h1 + α12h2 + α13h3
αij represents the attention weight for the decoder’s hidden state at time t=1 with respect to the encoder’s hidden state at position j.
Calculating Attention Weights:

A similarity score is computed between the current decoder hidden state (s1) and each encoder hidden state (hi):
scss
Copy code
score = dot_product(s1, hi)
The scores are passed through a softmax function to normalize them:
scss
Copy code
αij = softmax(score)
This ensures that the attention weights sum up to 1.
Using the Context Vector:
The context vector is combined with the decoder hidden state to generate the next output:

scss
Copy code
s2 = DecoderRNN(s1, y1, c1)
y2 = softmax(Linear(s2))
Example for Context:
Consider the sentence: "The animal couldn't cross the road because it was injured."
Here, the word "it" can refer to either "animal" or "road." The attention mechanism helps resolve such ambiguities by assigning higher weights to the relevant parts of the input sequence, ensuring that the model generates contextually accurate translations.

Summary:
The encoder-decoder architecture with attention dynamically adjusts focus based on the input sentence, enabling more accurate translations. By combining the power of sequential processing (RNNs) with a context-aware attention mechanism, this architecture significantly improves the quality of machine translation and similar tasks.


