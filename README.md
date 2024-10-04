# RNA Structure Prediction Using GRU in Keras

This project focuses on predicting RNA structural characteristics using a Bidirectional GRU (Gated Recurrent Unit) model. The data is preprocessed and fed into a GRU-based neural network, which outputs predictions for various RNA degradation metrics.

## Project Overview

This project utilizes sequential data representing RNA sequences to predict five degradation characteristics:
- `reactivity`
- `deg_Mg_pH10`
- `deg_Mg_50C`
- `deg_pH10`
- `deg_50C`

The RNA sequences are tokenized and converted into integer representations, which are then used as inputs to the GRU-based neural network.

### Key Features:
- **GRU Model**: A Bidirectional GRU model built using Keras, with embedding layers and spatial dropout for regularization.
- **MCRMSE Loss Function**: This loss function calculates the average RMSE across multiple columns, making it ideal for multi-output regression tasks.
- **Handling Mixed Sequence Lengths**: The model handles both 107 and 130 length sequences from the dataset, splitting the test set based on sequence length.
- **Training**: The model is trained with callbacks to reduce learning rates, as well as saving the best model checkpoints.

## Data Preprocessing

The dataset consists of RNA sequences represented in three columns:
1. `sequence`
2. `structure`
3. `predicted_loop_type`

These sequences are tokenized into integer arrays using a `token2int` dictionary, where each character is mapped to an integer. The target labels consist of five continuous variables representing degradation metrics of RNA sequences.

## Model Architecture

The model consists of the following layers:
1. **Input Layer**: Takes in a sequence of integers.
2. **Embedding Layer**: Converts integer tokens into dense vectors.
3. **Bidirectional GRU Layers**: Three layers of Bidirectional GRUs are used to capture dependencies in the sequences.
4. **Dense Output Layer**: A final dense layer outputs the predictions for each RNA sequence.

### Loss Function
The model uses the Mean Column-wise Root Mean Squared Error (MCRMSE) as the loss function, which is calculated across all predicted columns.

## Dataset

The dataset was sourced from **Kaggle**, specifically for the task of RNA degradation prediction. You can access the dataset at [Kaggle RNA Degradation Prediction Dataset](https://www.kaggle.com/competitions/stanford-covid-vaccine).

## Installation

Step 1: Clone the Repository
First, clone this repository to your local machine:

bash
git clone https://github.com/yourusername/covid19-mrna-degradation-prediction.git
cd covid19-mrna-degradation-prediction

Step 2: Download the Dataset
Download the RNA degradation dataset from the Kaggle competition. Place the dataset files in the data/ directory inside the cloned repository.

Step 3: Run the Model
To train the model and make predictions, execute the main.py file:
python main.py
This will load the data, preprocess it, train the Bi-GRU model, and output the predicted degradation values. The results will be saved in the results/ directory.

Step 4: Evaluate the Model
After training, the evaluation metrics (MCRMSE) will be displayed on the console. You can visualize the predicted degradation rates using the provided plotting functions.

To generate plots for the predicted values, run:
python visualize_results.py

## References
1. Pardi, N., Hogan, M. "mRNA vaccines — a new era in vaccinology." *NatRev Drug Discovery* (2018).
2. Kipf, T., Welling, M. "Semi-Supervised Classification with Graph Convolutional Networks." *arXiv* (2017).
3. Zhang, C., Maruggi, G., et al. "Advances in mRNA Vaccines for Infectious Diseases." *Frontiers in Immunology* (2019).
4. OpenVaccine: COVID-19 mRNA Vaccine Degradation Prediction. (n.d.). Kaggle. https://www.kaggle.com/competitions/stanford-covid-vaccine

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
