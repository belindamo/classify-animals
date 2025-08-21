# Data

This folder contains research data files for animal classification experiments.

## Directory Structure

```
data/
├── README.md          # This file
├── raw/               # Raw, unprocessed datasets
├── processed/         # Cleaned and preprocessed datasets
└── samples/           # Small sample datasets for testing
```

## Available Datasets

### Recommended Starting Datasets

1. **Animals-10** (Small-scale, recommended for prototyping)
   - 10 animal classes: cats, dogs, horses, spiders, butterflies, chickens, cows, squirrels, sheep, elephants
   - ~28,000 images total
   - Available on Kaggle: https://www.kaggle.com/datasets/alessiocorrado99/animals10
   - License: CC0 (Public Domain)

2. **CIFAR-10 Animal Classes** (Quick experimentation)
   - 6 animal classes from CIFAR-10: bird, cat, deer, dog, frog, horse
   - 6,000 images per class (32x32 pixels)
   - Built into PyTorch/TensorFlow
   - License: Open source

### Advanced Datasets

3. **Stanford Dogs Dataset** (Medium-scale, fine-grained)
   - 120 dog breeds, 20,580 images
   - Bounding box annotations available
   - Download: http://vision.stanford.edu/aditya86/ImageNetDogs/main.html
   - License: Research use

4. **Oxford-IIIT Pet Dataset** (Medium-scale, segmentation)
   - 37 pet categories (25 dogs, 12 cats)
   - ~200 images per class with segmentation masks
   - Download: https://www.robots.ox.ac.uk/~vgg/data/pets/
   - License: Academic use

5. **iNaturalist 2017** (Large-scale, challenging)
   - 859,000 images, 5,089 species
   - Real-world class imbalance
   - Research-grade benchmark dataset
   - License: Research use (registration required)

## Dataset Usage Guidelines

### For Initial Experiments
- Start with **Animals-10** or **CIFAR-10 animal classes**
- Quick to download and process
- Good for testing preprocessing pipelines

### For Research Publication
- Use **Stanford Dogs** for fine-grained classification research
- Use **Oxford-IIIT Pet Dataset** for segmentation + classification
- Use **iNaturalist** for large-scale, real-world challenges

### Data Loading Examples

```python
# For CIFAR-10 (built into PyTorch)
import torchvision.datasets as datasets
import torchvision.transforms as transforms

transform = transforms.Compose([
    transforms.Resize(224),
    transforms.ToTensor(),
    transforms.Normalize((0.485, 0.456, 0.406), (0.229, 0.224, 0.225))
])

# Filter for animal classes only
animal_classes = ['bird', 'cat', 'deer', 'dog', 'frog', 'horse']
cifar10 = datasets.CIFAR10(root='./data/raw', train=True, 
                          transform=transform, download=True)
```

```python
# For custom datasets
from torchvision.datasets import ImageFolder

# Assuming data organized in folders by class
dataset = ImageFolder(root='./data/processed/animals10', 
                     transform=transform)
```

## Preprocessing Notes

### Standard Preprocessing Pipeline
1. **Resize**: 224x224 for ImageNet-pretrained models, 32x32 for CIFAR experiments
2. **Normalization**: ImageNet statistics (0.485, 0.456, 0.406), (0.229, 0.224, 0.225)
3. **Data Augmentation**: Random crops, horizontal flips, color jitter for training

### Class Distribution Considerations
- **Balanced**: CIFAR-10, Animals-10
- **Imbalanced**: iNaturalist (reflects real-world distribution)
- **Few-shot**: Caltech-101 animal classes (limited samples per class)

## Storage Requirements

- **Animals-10**: ~500MB
- **CIFAR-10**: ~170MB
- **Stanford Dogs**: ~800MB
- **Oxford-IIIT Pet**: ~800MB
- **iNaturalist 2017**: ~150GB

## License Compliance

Ensure proper attribution and license compliance:
- **CC0/Open Source**: Animals-10, CIFAR-10
- **Academic Research Only**: Stanford Dogs, Oxford-IIIT Pet, iNaturalist
- **Registration Required**: ImageNet, iNaturalist

## Getting Started

1. Choose a dataset based on your research goals and computational resources
2. Download to the appropriate subdirectory (`raw/`, `processed/`, or `samples/`)
3. Follow the preprocessing guidelines in `section_notes/04-datasets.md`
4. Implement data loaders using the examples above
5. Start with baseline experiments before moving to advanced architectures