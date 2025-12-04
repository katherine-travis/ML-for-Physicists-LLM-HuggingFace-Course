# Summary of Chapter 4: Sharing Models and Tokenizers


## The Hugging Face Hub

Hugging Face provides a central platform called The Hugging Face Hub, where anyone can discover, use, and contribute new models and datasets. Each model is hosted as a Git repository, which allows versioning and reproducibility. Sharing a model on the Hub automatically deploys a hosted Inference API for that model. Anyone in the community can test models directly on their pages using custom inputs and appropriate widgets. Use of the Hub is free, but there are also paid plans available for private model sharing.

## Using Pretrained Models

The Model Hub allows users to instantiate models using the pipeline function by providing the model identifier as a parameter. The chosen checkpoint must be suitable for its intened task, as an inapproprate head for a given task will give nonsensical results. The Hub interface provides a task selector to help identify appropriate checkpoints. Auto classes are recommended because they are architecture-agnostic, making checkpoint switch simple and flexible; however, models can also be instantiated using specific architecture classes. Hugging Face recommends that when using a pretrained model, users verify how it was trained, what datasets were used for training, its limitations and biases etc. All of this information is available on the model card.

## Sharing Pretrained Models

All users can contribute by sharing their own trained models with the community. The goal is to save others time and compute resources while providing access to useful models. There are three ways to create new model repositories: using push_to_hub API (simplest approach, requires users to generate an authentication token for the huggingface_hub API to identify credentials and write access permissions), using the huggingface_hub Python library, and using the web interface. 

## Building a Model Card

The model card defines the model and ensures reusability by community members and reproducibility of results. The model card documents the training and evaluation process, provides information about data usage, preprocessing, and postprocessing. This enables users to identify and understand limitations, biases, and appropriate usage contexts of the model. 

Model cards begin with a high level overview followed by more detailed sections. These sections consist of model description, intended uses, limitations, how to use, training data, training procedure, variables and metrics, and evaluation results. The categories a model belongs to are identified according to metadata added in the model card header.
