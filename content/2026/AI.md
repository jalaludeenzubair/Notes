LIVE Notes

LLM generates 1 word at a time, and continues till end of response

![](assets/20260211_085616_image.png)

How model is trained - Weight adjustment

![](assets/20260211_085633_image.png)

Need of token in processing

![](assets/20260211_085642_image.png)

Vector Embedding to represent meaning of token

![](assets/20260211_085656_image.png)

Vector representing as point, in multiple dimensional space (1D, 2D, 3D)

![](assets/20260211_085719_image.png)

Representation in a D dimensional space

![](assets/20260211_085731_image.png)

Flow

![](assets/20260211_085743_image.png)

Embedding matrix for all tokens

![](assets/20260211_085752_image.png)

GPT transformer architecture

![](assets/20260211_085804_image.png)

What to expect from the model

![](assets/20260211_085828_image.png)

LLM Internals from basic - AI Engineering.

AI Engineering.

AI - 1950-1960

Can we make computers, softwares make intelligent decisions like humans

**AI Models**: Algo trained on large amount of data, they can perform specific taks

**GenAI** - Generative AI (all AI models - subset of AI model).

Generate new content text, audio, video, images..

Types of GenAI models

- LLM (Large language model)

text as input [LLM] generate text as ouput

- MultiModel LLM

text/images/audio [MM LLM] => text/images/output

- Image / video generation

=> images, videos

- voice => text
- text => voice
- Embedding models

OpenAI - ChatGPT

LLM Internal

AI Engineering more easy for you.

LLM - Large Language Model

Large - trained on large amount of data.

Language - Human language

OpenAI - GPT [Generative Pretrained Transformer Model]

Meta - Llama

LLM - GPT

chat-gpt (wrapper)

GPT

===========

How LLM does this..

Core concept

generate 1 word at a time.

Eat its own output

it generates 1 word at a time.

Appends that word to input, to predict the next word.

keep repeating till end of meaningful answer comes back.

=====

How to create such a great intelligence.. mimic human intelligence..

=====

1. Train your algorithms/logic so it can understand meaning, and repond with statement. it becomes intelligent
2. Using it.

=============

How to train this model.

The starting point of all achievement is DESIRE. Keep this constantly in mind. Weak desire brings weak results, just as a small fire makes a small amount of heat.

===

the model predicts the next word.

it will do loss calculation. compare predicted word with expected output.

back propogation - analyze how wrong you were

optimizer update (adman)- changes the value slightly and check if the right word is predicted.

we only tell input & output to machine.

we don't dictate what logic it should do for processing & giving that output.

that logic is decided by machine itself.

ML => DL => NN => GenAL

- parameters/weight - numeric value. decimal

  2.4, 5.3, 0, -5,.....

During during

- Model becomes intelligent.
- Final version of weight

==== during model training

input: The starting point of all

Out: achievement

model doesn't understand our plain words..

converts it into token

Token

word, part of word, 2 words together

model does optimization. if its supposed to process every possible word in English.. then many words might exist..

eat, eating, jump, jumping...

instead, model will choose to break "eat" "ing"

so will less words it can do everything..

=====

words => tokens.

===

every token will have a unquie Id

The starting point of all achievement is DESIRE. Keep this constantly in mind. Weak desire brings weak results, just as a small fire makes a small amount of heat.

=> converted into tokens

=> every token will have Id

Tokenization

WORK => TOKEN => TOKEN_ID

https://platform.openai.com/tokenizer

jumping

crying

[79879, 289, 198, 6985, 289]

jump => 79879

ing => 289

entry => 198

cry => 6985

ing => 289

===========

eat => food, mouth, chew, taste, energy, not_hungry, health

token are clear..

what is meaning of these tokens???

eat

吃

=================

how meaning can be assigned to token.

how can model understand meaning of "eat"

Embedding

- gives meaning to the tokens
- 2 token, which have similar meaning, should be considered as identical.

Embedding uses the concept of "vectors" to give meaning to the token.

vector : array of floating point numbers

[2.3, 4.5, 6.6, 0, -3,24, ......]

what should be the value of these vector numbers.. that is defined as embedding

embedding is special vector which gives meaning to token

vector - magnitude + direction

Models will have dimensions (how many number of values inside vector)

No. of Dimembers 4096

12000+

In LLM every token can be represented as D dimentional array/vector

the vector [3,2,5.... d] can be represented, as a point in a D dimention space

Embedding---------------

embedding gives meaning to the token

embedding uses vector for giving meaning

vector is array of decimal points

the values of this array is finalized by LLM during training, depending on current token is how much related with those other values.

this vector can be represented as point, in D dimentional space.

similar meaning vectors can be represented as points, which are close to each other in D dimention space.

Embedding Matrix - Meaning of all tokens will be there.

[T x D]

T - number of tokens

D - dimensions

matrix, where T(token) number of rows, and d number of dimension(columns) are available

1 x D

3 x 2

all tokens which are identified by the model is called as Model Vocabulary

When we do model training:

1. Model becomes intelligent
2. Weights/Parameters are finalized - 200 billions of parameters

weight adjustments

Self Attention

Feed Forward Neural Network

3. Modal vocabulary, id
4. Vector Embeddings

=========================================

# **Processing of LLM training**

- Data Collection – Gather large-scale text data.
- Tokenization – Break text into tokens for model input. (BPE)
- Embedding Initialization – Map tokens to vectors.
- Forward Pass – Pass data through transformer layers.
- Loss Calculation – Compare predictions vs. actual tokens.
- Backward Pass (Backpropagation) - figure out how wrong each weight was
- Optimizer Update – Update parameters (e.g., Adam). nudge the weights in the right direction to reduce future error.
- Repeat Over Epochs – train it on huge data until it gets good at language in general.
- Fine-tuning / Alignment – Adapt to specific tasks or safety needs.

========================

2. Using these trained models - "Inference phase"

2017 - Google LLM

Attention is all you Need.

How LLM can internally work for get intelligence..

OpenAI

GPT

Google published a paper.. on how LLM internal

how it can generate new stuff.

take input, predict new word.. and how continue to generate new content..

OpenAI - GPT

internals LLM

Encoder - Decoder

GPT - only decoder

LLM internally uses concept of Transformer to become generate new tokens..

LLM

GPT (OpenAI)

Generative Pretrained Transformer

took google initial proposal

only decoder

Tranformer

1. Attention computation (Multi Head Masked Attention)
2. FFN - Feed Forward Neural Network

Input token

Positional Embedding

which token is at what position

every position will have 1XD vector.

final matrix: N x D

2 concepts to fully understand meaning of incoming statement.

1. Multi Head attention
2. Transformer stacking

understand the meaning of the input statement.

I am going to bank to deposit \_\_\_

===========================================

Prompt execution - Major steps during Prompt Inference (when you send a prompt)

- Tokenization – Convert your prompt into tokens.
- Embedding Lookup – Map tokens to numerical vectors.
- Positional Embedding
- Forward Pass – Process through transformer layers (attention + feedforward).
- Logits Calculation – Project hidden state to vocabulary space.
- Softmax – Convert logits into probability distribution.
- Sampling / Decoding – Select next token (greedy, beam, top-k, etc.).
- Iterate Until Stop \*\*\*\*– Repeat until end-of-sequence or max tokens.

Detokenization – Convert tokens back into human-readable text.
