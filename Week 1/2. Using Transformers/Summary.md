# Summary of Chapter 2: Using Transformers

Chapter 2 of the Hugging Face LLM Course explores the Transformers library. The chapter is structured around six major sections built around understanding how to effectively use transformer models for natural language processing tasks.

## Behind the Pipeline

The first sections breaks the pipeline function into three steps: Preprocessing, passing inputs through the model, and postprocessing. In the preprocessing stage, input is tokenized; raw text is split into tokens which are mapped to numerical representations that neural networks can process. Some models require additional inputs to indicate the beginning or end of a sequence. The transformers library provides the AutoTokenizer class with a from_pretrained method that automatically retrieves the appropriate tokenizer configuration and caches it for future use.

The model processing stage involves working with hidden states. Hidden states are high dimensional vectors representing contextual understanding of inputs. The vector output by the transformer model is large and typically has three dimensions: batch size (the number of sequences processed at a time), sequence length (the length of the numerical representation of the sequence), and hidden size (the vector dimension of each model input). These hidden states are inputs to task-specific model heads which are composed of linear layers that project high dimensional vectors onto different dimensions for specific tasks. 

The postprocessing stage transforms logits (unnormalized scores from the final layer) into probabilities using SoftMax. These probabilities can be mapped back to readable labels, producing predictions with associated confidence scores.

## Models

The second section looks at the creation and use of transformer models through the AutoModel class. The AutoModel class automatically guesses the appropriate model architecture for a given checkpoint and instantiates it. Models can be initialized from scratch or loaded from pretrained checkpoints. Using pretrained models is typically recommended as it is more efficient to fine-tune a pretrained model than to train one from scratch. This section briefly touches on the environmental impact of training from scratch vs using a pretrained model.

## Tokenizers

Secrtion 3 explains various types of tokenization and their implementation. The chapter explores three approaches: word-based tokenization, where each word recieves a unique token, resulting in large vocabularies and treats similar words as unrelated; character-based tokenization, which produces smaller vocabularies but longer sequences and reduced semantic meaning; and subword tokenization, which keeps frequent words whole but decomposes rare words into meaningful components, resulting in a more balanced vocabulary size that preserves semantic meaning. The encoding process involves tokenization followed by conversion into input IDs using a vocabulary that must match the one used during model pretraining, while decoding reverses this process by converting indices back to readable strings. Specific implementations include Byte-level BPE used in GPT-2 and WordPiece used in BERT. 

## Handling Multiple Sequences

Certain practical challenges may be introduced when processing multiple inputs. Transformer models typically expect multiple sentences by default and require additional batch dimension for single sequences (you will see an instance of a single sequence input failing at the top of the 4_Handling_multiple_sequences notebook). Length variations between sequences can also result in the code failing because tensors require rectangular shapes. This is handled by padding sequences that are too short or truncating sequences that are too long. Attention masks use ones for tokens that should be attended to and zeroes for tokens that should be ignored (e.g. padding tokens), that way the model does not treat padding tokens as meaningful input.

## Putting it All Together

This section demonstrates how the Transformers API provides high-level functionality that handles all preprocessing steps automatically through a unified interface. When calling the tokenizer directly on sentences, it returns inpus ready for the model. The tokenizer handles single or multiple sequences, applies padding, performs truncation, and converts outputs to different framework tensors. Special tokens are automatically added because models were pretrained with them, ensuring consistent results during inference.

## Optimized Inference Deployment

The last section looks at advanced frameworks for production deployment. I did not read this section in detail.
