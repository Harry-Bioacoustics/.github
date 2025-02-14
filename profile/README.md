# Organisation Structure for Harry-Bioacoustics

## Repository Structure

### 1. `dataset-management`
   **Purpose:** Scripts and tools for collecting, processing, and managing audio datasets.
   - Raw data collection scripts (e.g., using `xeno-canto-py`)
   - Data preprocessing scripts (e.g., spectrogram generation with `librosa`)
   - Metadata handling tools

### 2. `model-training`
   **Purpose:** Training and evaluating machine learning models for dialect classification.
   - CNN-based model architectures
   - MixIT and BirdNet-based models
   - Training scripts and hyperparameter tuning
   - Model evaluation and benchmarking

### 3. `birdnet-integration`
   **Purpose:** Custom implementations and modifications of BirdNET for dialect analysis.
   - BirdNET model adaptations
   - API integrations
   - Experiment results with BirdNET's performance

### 4. `field-deployment`
   **Purpose:** Raspberry Pi setup, power management, and deployment strategies.
   - Raspberry Pi configuration and setup guides
   - Solar power management
   - Remote data collection and storage

### 5. `analysis-visualisation`
   **Purpose:** Tools for analysing and visualising model predictions and dataset trends.
   - Spectrogram visualisation scripts
   - Model performance dashboards
   - Statistical analysis tools
