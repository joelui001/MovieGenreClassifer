# MovieGenreClassifer
This project aims to develop a movie genre classification system based on a Large Language Model (LLM). Users can input a description of a movie, and the system will analyze the text to return a list of applicable genres.
## System Setup Instructions
To set up your system for the movie genre classification project, follow these steps:

1. **Set the API Key**: 
   - Open the source code file (main.ipynb) and set your API key in the first line. This key is essential for authenticating requests to any external services you may be using.

2. **Install Required Dependencies**: 
   - Install all necessary dependencies by running the `requirements.txt` file. Execute the following command:
     ```bash
     pip install -r requirements.txt
     ```
   - This will ensure that all required libraries are installed for the project.

3. **Execute the Code**: 
   - Run the main code file to start the application. Once executed, you can access the service at `https://127.0.0.1`, where you can input movie descriptions and receive a list of applicable genres in return.

## How To Use It?
### Example Usage
To classify a movie genre, you can use curl to send a POST request:
```
curl -X POST http://127.0.0.1:5000/classify \
-H "Content-Type: application/json" \
-d '{"description": "A young wizard embarks on an adventure to defeat a dark sorcerer."}'
```
Response Format
The API will return a JSON response containing the list of genres:
```
{
  "genres": ["Fantasy", "Adventure", "Action"]
}
```
## Discussion
### Algorithm Selection
Movie classification for genres is a multi-label classification problem in which a single film can belong to multiple genres simultaneously. Below is the comparsion table of the common approach for multi-label classification problems.

### Summary of Multi-Label Classification Methods
### Comparison of Text Classification Methods

| Method                     | Pros                                                                                     | Cons                                                                                      |
|----------------------------|------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| **Naive Bayes**            | - Simple to implement and computationally efficient.                                    | - Assumes feature independence, which may not hold in real-world data.                  |
|                            | - Performs well with high-dimensional data and limited training samples.                | - Can assign zero probability to unseen events, leading to poor generalization.          |
| **Support Vector Machines (SVM)** | - Effective in high-dimensional spaces and with clear margin of separation.        | - Memory-intensive and slower to train on large datasets.                                |
|                            | - Robust against overfitting, especially in high-dimensional space.                     | - Less effective on noisy data and when the number of features exceeds the number of samples. |
| **K-Nearest Neighbors (KNN)** | - Simple and intuitive; no training phase required.                                   | - Computationally expensive during prediction time as it requires distance calculations for all instances. |
|                            | - Naturally accommodates multi-label outputs by considering nearest neighbors.          | - Sensitive to irrelevant features and noise in the data.                                 |
| **Logistic Regression**    | - Easy to implement and interpret; provides probabilities for class membership.         | - Assumes linear relationship between features and the log-odds of the outcome.          |
|                            | - Works well with binary and multi-class classification problems.                       | - May underperform with complex relationships between features.                          |
| **Large Language Models (LLMs)**  | - Excellent contextual understanding and ability to capture nuanced meanings.      | - Resource-intensive, requiring significant computational power for training and inference.|
|                            | - Zero-shot learning capabilities reduce the need for extensive retraining on labeled data.| - Complexity in fine-tuning and adapting models to specific tasks.                       |

### Summary

Among these methods, **Large Language Models (LLMs)** are selected for text classification tasks, when dealing with complex datasets that require nAanced understanding of context and relationships within the text. Their ability to perform zero-shot learning allows them to adapt to new categories without extensive retraining, making them highly versatile compared to traditional methods.

## Model Selection
Here are the reasons for selecting Qwen2-7B:
   - **Open Source**: Qwen2-7B is the leading open-source LLM under the Apache 2.0 license, allowing for unrestricted commercial use.
   - **Performance vs. Cost**: With 7 billion parameters, it balances high performance and low operational costs, providing businesses with a powerful AI solution without the high costs associated with proprietary models like GPT-4, making it accessible for businesses.
   - **Flexible Deployment**: Can be deployed locally for data control or accessed via the Alibaba API for ease of integration.
   - **Multilingual Support**: Supports multiple languages, enhancing its utility for global applications and diverse audiences.
   - **Customization Options**: Offers extensive customization capabilities, enabling users to fine-tune the model on specific datasets for improved performance in targeted applications, making it more adaptable than many other models
   - **Robust Community Support**: Being open-source, Qwen2-7B benefits from community contributions and ongoing improvements, which can lead to quicker updates and enhancements compared to closed-source alternatives
### Model Performance
| **Model**       | **MMLU** | **GPQA** | **Theorem QA** | **BBH** | **HellaSwag** |
|------------------|----------|----------|----------------|---------|----------------|
| **Qwen2-7B**     | 70.3     | 31.8     | 31.1           | 62.6    | 80.7           |
| **Mistral-7B**   | 64.2     | 24.7     | 19.2           | 56.1    | 83.2           |
| **Llama-3-8B**   | 66.6     | 25.8     | 22.1           | 57.7    | 82.1           |

## Potential Improvements and Extensions
To enhance the performance of the current movie genre classification system, several potential improvements and extensions could be considered. The following strategies could be implemented:
1. Fine-Tuning the Model:
   - Domain-Specific Fine-Tuning: By fine-tuning the model on a curated dataset of movie descriptions and their corresponding genres, we can improve its accuracy in genre classification and the model to better understand the nuances specific to movie-related language.
2. Online Search Integration:
   - Adding functionality for the model to search online databases (e.g., IMDb, Rotten Tomatoes) for real-time information about movies would ensure accuracy in genre classification by providing up-to-date data and context.
3. Expanded User Input Options:
   - Implementing a feature that allows the system to automatically classify any user input, no matter it’s a title, production company name, or user review. The model would analyze the nature of the text provided and estimate relevant genres based on its understanding of context and relationships within the input.
