# Plant Leaf Classification with ANN and CNN Models

A computer vision notebook that explores fully connected neural networks and a convolutional neural network for classifying plant leaf images. It covers image loading, resizing, normalization, neural-network training and prediction visualization using TensorFlow/Keras.

## Project contents

- `PlantVillage_With_ANN & CNN.ipynb`: image preparation, three fully connected model experiments, a CNN experiment and evaluation plots.

The image dataset, trained checkpoints and example external image are not included in the repository.

## Dataset

The notebook loads a local PlantVillage directory organized into one subfolder per class:

```text
PlantVillage/
  class_a/
    image_1.jpg
    image_2.jpg
  class_b/
    image_3.jpg
```

The saved run loads 20,638 valid images across 15 classes. These counts describe the particular dataset used in the notebook, not every version of PlantVillage.

Images are resized to `128 x 128` RGB pixels and normalized by dividing pixel values by 255. Labels are derived from directory names and converted to one-hot vectors.

## Experiments

### Fully connected neural networks

Three architectures flatten the input image and use Dense layers with ReLU activations, BatchNormalization, Dropout and a softmax classification output. Training uses image augmentation, Adam, categorical cross-entropy, early stopping and model checkpointing.

### Convolutional neural network

The CNN uses four convolution blocks with BatchNormalization, max pooling and Dropout, followed by a dense classification head. Its output layer is hard-coded for 15 classes. The saved training setup runs for up to five epochs.

An image-augmentation generator is defined in the CNN section, but the CNN training call uses the original training arrays rather than that generator.

### Visualizations

The notebook includes training curves, confusion matrices, classification reports and displays of true versus predicted class indices.

## Evaluation status

The current notebook does not provide a reliable held-out comparison of the models:

- In both the fully connected and CNN workflows, the original test arrays are overwritten with training arrays before validation and evaluation.
- The CNN metric section calculates scores using an earlier `y_pred` variable instead of deriving new class predictions from `y_pred_proba`.

For these reasons, the saved values should not be presented as independent test accuracy, and the notebook does not support a claim of 97% held-out CNN accuracy. A clean evaluation is needed before publishing a model-performance comparison.

## Run locally

1. Download or clone this repository.
2. Install the main dependencies:

   ```bash
   pip install jupyter tensorflow numpy pandas matplotlib seaborn pillow scikit-learn
   ```

3. Obtain the image dataset separately and keep its class-subfolder structure.
4. Replace the local Windows path in `data_dir` with your dataset directory.
5. Open the notebook:

   ```bash
   jupyter notebook "PlantVillage_With_ANN & CNN.ipynb"
   ```

6. Apply the evaluation fixes below before rerunning the experiments. Update or skip the external-image example if its image file is unavailable.

The notebook loads images into memory, so training can require substantial RAM and computing time. Package versions are not pinned.

## Evaluation fixes before reporting results

1. Preserve separate training, validation and test sets; remove the assignments that replace test arrays with training arrays.
2. Use a consistent, saved class-name mapping and set the final CNN layer size from `num_classes`.
3. Derive CNN class predictions from its own probability output before calculating metrics.
4. Select models with validation data, then evaluate once on the untouched test set.
5. Report per-class metrics and inspect performance on images captured outside the training dataset.

## Scope

This is an experimental image-classification project, not a validated agricultural diagnostic tool. Performance on controlled leaf images does not establish reliability on field photographs.
