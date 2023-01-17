# Attention-DNN
Attention-based End-to-End Speech-to-Text Deep Neural Network


<ins>Objective</ins>: In this project we learn to build neural networks for sequence-to-sequence conversion or transduction. 
“Sequence-to-sequence” conversion refers to problems where a sequence of inputs goes into the system, which emits a sequence of outputs in response. The need for such conversion arises in many problems, e.g. 

• Speech recognition: A sequence of speech feature vectors is input. The output is a sequence of characters writing out what was spoken. 
• Machine translation: A sequence of words in one language is input. The output is a sequence of words in a different language. 
• Dialog systems: A user’s input goes in. The output is the system’s response. 

We work on the speech recognition problem, since we’re already familiar with the data prior Speech Recognition projects. However, here we learn to directly spell the spoken sentence out in the English alphabet. A key characteristic of such problems is that there may be no obvious correspondence between the input and the output sequences. 

For instance, in a dialog system, a user input “my screen is blank” may elicit the output “check the power switch”. Or, more related to the problem of this homework, in a speech recognition system the input may be the (feature vector sequence for the) spoken recording for the phrase “know how”. The system output must be the character sequence “k”, “n”, “o”, “w”, “ ”, “h”, “o”, “w” (note the blank space “ ” between know and how – the output is supposed to be readable, and must include blank spaces as characters). There is no obvious audio corresponding to the silent characters “k” and “w” in know, or the blank space character between know and how, yet these characters must nevertheless be output. 

As a consequence of the absence of correspondence between the input and output sequences, the usual “vertical” architectures that we have used so far in our prior projects, where the input is sequentially processed by layers of neurons until the output is finally computed, can no longer be used. Instead, we must use a two-component model, comprising two separate network blocks, one to process the input, and another to compute the output. Such architectures are called encoder-decoder architectures. 

![ip](https://user-images.githubusercontent.com/92863991/212872452-d8b2af33-303f-4051-9e32-db2f4a570db9.png)


The encoder processes the input sequence to compute feature representations (embeddings) of the input sequence. The decoder subsequently uses the input representations computed by the encoder to sequentially compute the output de novo, i.e. from scratch (Figure 1b). The most important part of the model is the attention mechanism. Although the decoder’s output may not have a direct correspondence with the input, each individual output symbol (character) nonetheless relates more to some parts of the input than others, e.g. the blank character “ ” in our above speech recognition example corresponds primarily to the audio at the boundary between the words “know” and “how” in the recording. When outputting the “ ”, the decoder must somehow know to “focus” on, or “pay attention” to this region of the input. In this homework you will learn how to build an encoder to effectively extract features from a speech signal, how to construct a decoder that can sequentially spell out the transcription of the audio, and how to implement an attention mechanism between the decoder and the encoder.

![att](https://user-images.githubusercontent.com/92863991/212872453-438f8c8f-ac01-47f6-b25c-328136cdfc10.png)


Although the specifics of the homework will be targeted towards speech recognition, please note that the general framework (with appropriate modification of the encoder and decoder architectures) should also apply to other types of sequence-to-sequence problems, or even to image or video captioning (you would only need to modify the encoder to derive features from images or video respectively).

<ins>Output format</ins>: 

![op](https://user-images.githubusercontent.com/92863991/212872449-dba9ed04-b3fb-418d-a580-49eca8116717.png)
