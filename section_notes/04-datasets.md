

# Datasets

## Overview

This section documents datasets suitable for animal classification experiments, following Computer Science-inspired research methodology. The datasets are categorized by scale and complexity to support different stages of research and development.

## Available Datasets

### Large-Scale Datasets

#### iNaturalist 2017 Challenge Dataset
- **Name**: iNaturalist Challenge 2017
- **Source**: [iNaturalist](https://www.inaturalist.org/), [CVPR 2018 Paper](https://openaccess.thecvf.com/content_cvpr_2018/papers/Van_Horn_The_INaturalist_Species_CVPR_2018_paper.pdf)
- **Size**: 859,000 images, 5,089 species (plants and animals)
- **Features**: Real-world images with class imbalance, varying quality, citizen science verified
- **License**: Research use (non-commercial)
- **Preprocessing**: Images vary in resolution, require normalization and augmentation
- **Baseline**: 67% top-1 accuracy with non-ensemble methods
- **Use Case**: Large-scale species classification with real-world distribution

#### ImageNet (Animal Classes)
- **Name**: ImageNet Animal Subset
- **Source**: [ImageNet](https://www.image-net.org/)
- **Size**: Subset of 1.2M+ images from animal-related WordNet synsets
- **Features**: High-resolution images, hierarchical organization
- **License**: Research use (registration required)
- **Preprocessing**: Standard ImageNet preprocessing (224x224, normalization)
- **Use Case**: Transfer learning source for animal classification

### Medium-Scale Datasets

#### Stanford Dogs Dataset
- **Name**: Stanford Dogs Dataset
- **Source**: [Stanford Vision Lab](http://vision.stanford.edu/aditya86/ImageNetDogs/main.html)
- **Size**: 20,580 images, 120 dog breeds
- **Features**: Fine-grained categorization, bounding box annotations
- **License**: Research use
- **Preprocessing**: Images ~300x200 pixels, bounding box cropping recommended
- **Use Case**: Fine-grained animal classification, breed identification

#### Oxford-IIIT Pet Dataset
- **Name**: Oxford-IIIT Pet Dataset
- **Source**: [Oxford VGG](https://www.robots.ox.ac.uk/~vgg/data/pets/)
- **Size**: ~7,400 images, 37 categories (25 dogs, 12 cats)
- **Features**: Head ROI annotations, trimap segmentation masks
- **License**: Academic use
- **Preprocessing**: ~200 images per class, head bounding boxes available
- **Use Case**: Pet classification, segmentation tasks

#### CIFAR-10 (Animal Classes)
- **Name**: CIFAR-10 Animal Subset
- **Source**: [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html)
- **Size**: 24,000 images from 4 animal classes (bird, cat, deer, dog, frog, horse)
- **Features**: 32x32 pixels, 6,000 images per class
- **License**: Open source
- **Preprocessing**: Small resolution, data augmentation essential
- **Use Case**: Baseline experiments, quick prototyping

#### CIFAR-100 (Animal Classes)
- **Name**: CIFAR-100 Animal Subset
- **Source**: [CIFAR-100](https://www.cs.toronto.edu/~kriz/cifar.html)
- **Size**: Animal-related classes from 100 total categories
- **Features**: 32x32 pixels, 600 images per class
- **License**: Open source
- **Preprocessing**: Limited resolution, hierarchical labels available
- **Use Case**: Multi-level classification experiments

### Small-Scale Datasets

#### Animals-10 Dataset
- **Name**: Animals-10
- **Source**: [Kaggle](https://www.kaggle.com/datasets/alessiocorrado99/animals10)
- **Size**: ~28,000 images, 10 animal classes
- **Features**: cats, dogs, horses, spiders, butterflies, chickens, cows, squirrels, sheep, elephants
- **License**: CC0 (Public Domain)
- **Preprocessing**: Variable resolution, requires resizing and normalization
- **Use Case**: Educational projects, baseline experiments

#### Caltech-101 (Animal Classes)
- **Name**: Caltech-101 Animal Subset
- **Source**: [Caltech Vision Lab](http://www.vision.caltech.edu/Image_Datasets/Caltech101/)
- **Size**: ~15 animal categories from 101 total classes
- **Features**: 40-800 images per category, object outlines available
- **License**: Academic research
- **Preprocessing**: ~300x200 pixels, cropped and annotated
- **Use Case**: Few-shot learning, object recognition baselines

## Benchmarks and Baselines

### Standard Benchmarks

1. **iNaturalist Challenge**: Annual competition with state-of-the-art results
   - Best methods achieve ~67% top-1 accuracy
   - Focus on class imbalance and long-tail distribution

2. **Stanford Dogs Fine-Grained Classification**:
   - Baseline: ~50% accuracy with traditional methods
   - SOTA: >90% with modern CNNs

3. **CIFAR-10 Animal Classes**:
   - Traditional baselines: 70-80% accuracy
   - Modern methods: >95% accuracy

### Evaluation Metrics

- **Top-1 Accuracy**: Primary metric for single-label classification
- **Top-5 Accuracy**: Relevant for fine-grained classification
- **Per-class F1 Score**: Important for imbalanced datasets
- **Mean Average Precision (mAP)**: For hierarchical classification

## Data Access Instructions

### Download and Setup

1. **Create data directory structure**:
   ```bash
   mkdir -p data/{raw,processed,samples}
   ```

2. **Large datasets** (iNaturalist, ImageNet):
   - Register for academic access
   - Download via official APIs or torrents
   - Expect 10-100GB+ storage requirements

3. **Medium datasets** (Stanford Dogs, Oxford Pets):
   - Direct download from official sources
   - 1-5GB storage requirements

4. **Small datasets** (Animals-10, CIFAR):
   - Available via Kaggle, PyTorch datasets, or direct download
   - <1GB storage requirements

### Preprocessing Pipeline

1. **Image normalization**: Convert to standard format (RGB, 0-1 range)
2. **Resizing**: Standard sizes (224x224 for ImageNet models, 32x32 for CIFAR)
3. **Data augmentation**: Random crops, flips, rotations for training
4. **Train/validation/test splits**: Follow standard splits or create 70/15/15 splits

### Quick Start Recommendations

- **For prototyping**: Start with Animals-10 or CIFAR-10 animal classes
- **For publication**: Use Stanford Dogs or Oxford-IIIT Pet Dataset
- **For large-scale research**: Progress to iNaturalist Challenge dataset
- **For transfer learning**: Pre-train on ImageNet, fine-tune on target dataset

