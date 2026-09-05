# Image Captioning AI

An image captioning system that combines **Computer Vision** and **Natural Language Processing** to automatically generate descriptive captions for images.

The project uses a **pre-trained ResNet-50** model to extract visual features from images and an **LSTM-based decoder** to generate captions from those features. A **Gradio** interface will provide a simple way to upload an image and generate its caption.

## Architecture

```text
                    Image
                      │
                      ▼
              ┌───────────────┐
              │  ResNet-50    │
              │ Pre-trained   │
              └───────┬───────┘
                      │
                      ▼
              Image Feature Vector
                      │
                      ▼
              ┌───────────────┐
              │     LSTM      │
              │ Caption       │
              │ Decoder       │
              └───────┬───────┘
                      │
                      ▼
                Generated Caption
                      │
                      ▼
              ┌───────────────┐
              │    Gradio     │
              │      UI       │
              └───────────────┘
```

### How it works

1. An image is provided as input.
2. The image is preprocessed using the transformations expected by ResNet-50.
3. A pre-trained ResNet-50 extracts a high-level visual representation of the image.
4. The final classification layer of ResNet-50 is replaced with an identity layer so that its feature representation can be used instead of class predictions.
5. The extracted feature vector is passed to an LSTM-based caption decoder.
6. The LSTM generates the caption sequentially, predicting one token at a time.
7. The generated token sequence is converted back into natural language.
8. The final caption is displayed through a Gradio web interface.

## Example

**Input:**

```text
[Image of a dog running through a field]
```

**Generated caption:**

```text
A dog is running through a field.
```

*The example above illustrates the intended output format; actual captions depend on the trained model.*

## Technologies

* **Python** — primary programming language
* **PyTorch** — neural network implementation and training
* **Torchvision** — ResNet-50 and image preprocessing
* **Pillow** — image loading and processing
* **tqdm** — training progress visualization
* **Gradio** — interactive web interface

## Dataset

The project is designed to use the **Flickr8k** image-caption dataset.

Flickr8k contains thousands of images, with multiple natural-language captions associated with each image. These image-caption pairs provide the training data needed to learn the relationship between visual features and language.

The dataset is used to train the LSTM caption decoder while the ResNet-50 encoder uses pre-trained weights.

The application will provide an interface where an image can be uploaded and a generated caption can be displayed.

## Training Pipeline

The training process consists of two major components:

### 1. Image Encoder

A pre-trained ResNet-50 is used to convert an image into a numerical feature representation.

```text
Image
  ↓
Preprocessing
  ↓
ResNet-50
  ↓
2048-dimensional feature representation
```

The ResNet-50 weights are pre-trained, so the project does not train the entire vision model from scratch.

### 2. Caption Decoder

The extracted image representation is combined with caption tokens and provided to an LSTM decoder.

```text
Image Features + Previous Tokens
                ↓
              LSTM
                ↓
           Next Token
                ↓
           Next Token
                ↓
              ...
                ↓
             <END>
```

Special tokens such as `<START>`, `<END>`, `<PAD>`, and `<UNK>` are used to represent the beginning/end of captions, padding, and unknown words.

## Current Status

🚧 **Under development**

Planned milestones:

* [ ] Set up project environment
* [ ] Prepare Flickr8k dataset
* [ ] Implement image preprocessing
* [ ] Extract image features using ResNet-50
* [ ] Build caption vocabulary
* [ ] Implement caption tokenization
* [ ] Implement LSTM decoder
* [ ] Train captioning model
* [ ] Implement caption generation
* [ ] Evaluate generated captions
* [ ] Build Gradio interface
* [ ] Test end-to-end image captioning
* [ ] Complete documentation

## Future Improvements

Possible improvements after the initial implementation include:

* Beam search for improved caption generation
* Attention mechanisms
* Transformer-based caption decoder
* Fine-tuning the image encoder
* Better caption evaluation metrics such as BLEU
* Improved UI and visualization
* Support for additional datasets

## Learning Objectives

This project demonstrates the integration of multiple areas of machine learning:

* Computer Vision
* Natural Language Processing
* Transfer Learning
* Convolutional Neural Networks
* Recurrent Neural Networks
* LSTM architectures
* Word embeddings
* Sequence generation
* Model training and inference
* Deep-learning application deployment
