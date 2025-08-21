# Modern Animal Classification using Deep Learning

## Key Papers

### 1. Evaluating Deep Learning Models for African Wildlife Image Classification: From DenseNet to Vision Transformers (2025)
**Authors**: Aliyu et al.
**Source**: arXiv:2507.21364

**Problem**: Wildlife populations in Africa face severe threats with vertebrate numbers declining by over 65% in the past five decades. Traditional monitoring relies on labor-intensive field surveys and manual camera trap image reviews.

**Prior Assumptions**: Previous work assumed that standard computer vision models could directly transfer to wildlife monitoring without domain-specific considerations.

**Insight**: The paper demonstrates that different architectures have vastly different performance characteristics in wildlife domains - Vision Transformers (ViT-H/14) achieved 99% accuracy vs DenseNet-201 at 67% accuracy, but with significantly higher computational costs.

**Technical Approach**: 
- Comparative evaluation of DenseNet-201, ResNet-152, EfficientNet-B4, and Vision Transformer ViT-H/14
- Transfer learning with frozen feature extractors
- Dataset: 4 species (buffalo, elephant, rhinoceros, zebra)

**Evaluation**: Accuracy-based evaluation with computational cost analysis

**Impact**: Highlights critical trade-offs between accuracy, resource requirements, and deployability in conservation settings. Deployed best-performing CNN to Hugging Face Gradio Space for real-time field use.

### 2. Multi-Species Object Detection in Drone Imagery for Population Monitoring of Endangered Animals (2024)
**Authors**: Sankaran, Sowmya
**Source**: arXiv:2407.00127

**Problem**: Animal populations worldwide are rapidly declining, requiring accurate counting of endangered species for monitoring population changes over time.

**Prior Assumptions**: Earlier work assumed that general object detection models (like baseline YOLOv8) would work well on drone imagery of wildlife.

**Insight**: Fine-tuning with domain-specific data and techniques can dramatically improve performance - from 0.7% accuracy (baseline YOLOv8) to 95% accuracy on safari animals.

**Technical Approach**:
- Fine-tuned YOLOv8 architecture with 30 different models
- Largest model: 43.7M parameters, 365 layers
- Hyperparameter tuning and data augmentation
- Deployment on Jetson Orin Nano for real-time inference

**Evaluation**: Accuracy on safari animal dataset, real-time performance metrics

**Impact**: Demonstrates feasibility of accurate real-time species detection on low-power drone platforms for population monitoring.

### 3. Evaluating Transfer Learning in Deep Learning Models for Wildlife Classification (2024)
**Authors**: Sharma, Dhakal, Bhavsar
**Source**: arXiv:2408.00002

**Problem**: Biodiversity decline due to poaching and human activities requires automated monitoring systems to replace error-prone, labor-intensive human monitoring.

**Prior Assumptions**: Traditional CNN architectures would be sufficient for wildlife classification tasks.

**Insight**: YOLOv8 can surpass other architectures (DenseNet, ResNet, VGGNet) in wildlife classification when properly applied with transfer learning.

**Technical Approach**:
- Custom dataset from iNaturalist and ZooChat
- Transfer learning by freezing pre-trained weights, replacing output layers
- Comparative evaluation across multiple architectures

**Evaluation**: Training accuracy (97.39%) and F1 score (96.50%) for YOLOv8

**Impact**: Suggests YOLOv8 integration could revolutionize wildlife monitoring with high accuracy and efficiency.

## Key Themes and Patterns

### Architecture Performance Patterns
- **Vision Transformers**: Highest accuracy but computationally expensive
- **DenseNet**: Good balance of accuracy and efficiency for CNNs  
- **YOLOv8**: Strong performance, especially with proper fine-tuning
- **Transfer Learning**: Critical for success across all approaches

### Domain-Specific Challenges
- **Data scarcity**: Limited labeled wildlife datasets
- **Environmental conditions**: Varying lighting, weather, backgrounds
- **Computational constraints**: Need for edge deployment in remote areas
- **Species variability**: High intra-species and inter-species variation