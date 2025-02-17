# TG4ncRNA
Predicting Functional Variants in Non-Coding RNA with Graph Attention Networks.


This repository presents TG4ncRNA, a deep learning framework designed to predict functional variants in non-coding RNA (ncRNA) by leveraging Graph Attention Networks (GAT). The model integrates multi-modal data, such as RNA sequence, secondary structure, chemical modifications, and protein interactions, to predict functional sites with high accuracy. TG4ncRNA utilizes the power of Tensor Fusion Networks (TFN) combined with hierarchical GAT to capture complex interactions between these data modalities.

Key Features
Multi-Modal Data Integration: Efficiently integrates RNA sequence, secondary structure, chemical modifications, and protein interactions using TFN.
Graph Attention Networks (GAT): Employs hierarchical GAT architecture to extract local and global patterns from multi-modal data.
Functional Variant Prediction: Focuses on predicting functional variants in ncRNA, with an emphasis on non-coding RNA regulatory sites.
Model Explainability: Enhances interpretability by visualizing attention weights and conducting adversarial perturbation analysis to assess model dependency on critical features.
Experimental Workflow
Data Preparation:

Gather RNA sequences, secondary structure, chemical modifications, and protein interaction data.
Preprocess the data (e.g., one-hot encoding for sequences, domain partitioning for structure, and embedding for proteins).
Model Construction:

Base Layer: Independently process sequence and structure features using GAT to capture local patterns.
TFN Fusion Layer: Integrate sequence and structure data using Tensor Fusion Networks (TFN).
Domain Layer: Generate functional domain super-nodes from the integrated features.
Global Layer: Combine functional domain features with protein interaction data to predict functional variants.
Training & Evaluation:

Multi-task loss function for joint optimization of functional variant prediction, base modification prediction, and domain classification.
Evaluation based on AUC-ROC, F1-score, and classification accuracy.
5-fold cross-validation to ensure robustness and stability of the model.
Interpretability:

Visualize TFN fusion weights to identify key inter-modal interactions.
Use adversarial perturbation analysis to measure the model's dependence on important features.
Usage
Install Dependencies:
bash
复制
编辑
pip install -r requirements.txt
Data Preparation:

Place your RNA sequence, structure, chemical modification, and protein interaction data in the data/ directory.
Preprocess the data using the provided preprocessing scripts (data_preprocessing.py).

Train the Model:

To train the model, use the following command:

python train.py --data_path ./data --epochs 50 --batch_size 32

Evaluate the Model:

To evaluate the model, use the command:

python evaluate.py --model_path ./model --test_data ./data/test
Potential Issues & Solutions
Missing Modalities:

Handle missing data through interpolation (e.g., KNN or mean filling).
Use adversarial training to improve model robustness when some modalities are missing.
High Computational Complexity:

Use low-rank decomposition techniques (CP or Tucker) to reduce the computational burden.
Implement mixed-precision training (FP16) to accelerate the training process.
Overfitting:

Apply regularization methods such as dropout and weight decay.
Use data augmentation strategies like random mutations and perturbations in secondary structure.
Modality Alignment Challenges:

Use adversarial alignment and contrastive learning to resolve modality misalignment issues.
Results
Performance: The TFN-GAT model significantly outperforms baseline models, especially for complex ncRNA sequences like lncRNAs.
Explainability: Attention heatmaps reveal key interactions between sequence and structure, aiding in functional site localization.
Robustness: The model remains effective even with missing or noisy modality data.
Future Directions
Extended Modalities: Incorporate new data types such as single-cell RNA-seq and chromatin accessibility data (e.g., ATAC-Seq).
Cross-Species Transfer: Transfer knowledge from model organisms like Drosophila or mice to human data for broader applicability.
Dynamic Modeling: Introduce temporal dimensions to capture the dynamics of ncRNA function in developmental or disease processes.
Citation
If you use this framework in your research, please cite the following paper:



This project is licensed under the MIT License - see the LICENSE file for details.


