Module Description
This module is a practical introduction to building AI models that can be applied to various infosec domains. It covers setting up a controlled AI environment using Miniconda for package management and JupyterLab for interactive experimentation. Students will learn to handle datasets, preprocess and transform data, and implement structured workflows for tasks such as spam classification, network anomaly detection, and malware classification. Throughout the module, learners will explore essential Python libraries like Scikit-learn and PyTorch, understand effective approaches to dataset processing, and become familiar with common evaluation metrics, enabling them to navigate the entire lifecycle of AI model development and experimentation.
Module Summary
Cybersecurity professionals rely on a well-structured AI environment and streamlined workflows to efficiently process data, build models, and extract insights. This module provides a direct path to establishing and optimizing such an environment — from installing and managing packages with Miniconda, to leveraging JupyterLab for interactive development and using libraries like Scikit-learn and PyTorch for model training and evaluation — ensuring students can move seamlessly from raw data to actionable models.

While this module offers an accompanying VM to solve the labs, its performance is limited and may result in longer training times. Therefore, we recommend setting up your personal environment on your own machine, which requires at least 4GB of RAM. Additionally, training benefits from GPU utilization; however, training on a CPU is also possible. We recommend a reasonably modern CPU with as many cores as possible for a decent training performance. In the majority of cases, your own environment will provide faster training times than the accompanying VM.

Key areas covered include:

Environment Setup: Establishing a dedicated AI environment using Miniconda for dependency management.
JupyterLab: Leveraging an interactive and flexible development platform for exploratory data analysis, rapid prototyping, and in-depth experimentation.
Python Libraries for AI: Applying Scikit-learn and PyTorch to model training, evaluation, and continuous improvement.
Datasets: Understanding key attributes of datasets, exploring their structure, identifying challenges, and learning how to load and inspect data to detect potential issues.
Data Preprocessing: Implementing rigorous methods to clean and refine data, including identifying invalid values, imputing missing entries, encoding categorical features, and handling skewed distributions.
Data Transformation: Applying transformations like one-hot encoding and data splitting to prepare data for downstream modeling tasks.
Spam Classification: Using Naive Bayes to translate raw text into representative numerical features for effective classification.
Network Anomaly Detection: Using random forests and specialized datasets like NSL-KDD to detect abnormal network behavior.
Malware Classification: Transforming malware samples into representational data (e.g., images) and using deep learning models like ResNet50 to classify malicious binaries, reinforcing complex feature extraction and model training techniques.
