# Summary of Chapter 10: Curate High-Quality Datasets

Chapter 10 teaches how to use Argilla to annotate and curate datasets for training and evaluating models. Existing Hub datasets may not align with specific applications or use cases, necessitating custom dataset creation and curation. Argilla allows users to turn unstructured data into structured data for NLP tasks.

## Set Up Your Argilla Instance

You can create an Argilla Space through Hugging Face by following a configuration form, with the option to enable persistent storage. After deployment, users log in with credentials and install the Argilla Python SDK using pip install argilla. Connecting to the Argilla instance requires the API URL, the API key, and optionally a Hugging Face token with write permissions for private spaces. To verify connection, call client.me, which should return user information if properly configured.

## Load Your Dataset to Argilla

Define settings that represent annotation tasks. This chapter shows how to use a news dataset to complete two tasks: text classification on topics and token classification for named entity identification. Settings include fields and questions. For text classification, LabelQuestion uses unique values from existing label columbs as options, ensuring compatibility with pre-existing labels. For token classification, SpanQuestion defines entity labels like person, organization, location, and event. After defining settings, datasets are created using rg.Dataset with the specified configuration and settings. Pre-existing labels can be mapped as pre-annotations.

## Annotate Your Dataset

Before beginning annotation, teams should establish alignment through annotation guidelines written in the dataset settings page. Guidelines help align teams on tasks and label usage. For tasks without suggestions like token classification, annotators manually add all labels by selecting text spans and assigning appropriate entity types. As annotators progress through records, they can submit responses when complete, save as drafts, or discard records that shouldnt be included in the dataset or wont receive responses.

