# POS Tagging Project: Rule-Based, CRF, BiLSTM-CRF, and BERT Comparison

This project implements and compares various approaches (Rule-Based, CRF, BiLSTM-CRF, fine-tuned BERT) for Part-of-Speech (POS) tagging on the UD_English-GUM (English) and UD_Telugu_English-TECT (Telugu-English code-mixed) datasets.

This guide provides instructions on how to set up the necessary Python environment and install dependencies to run this project.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

1.  **Python 3.10.17**: The project was developed and tested with this specific version (as indicated by notebook metadata/comments). While other Python 3.10.x versions (like 3.10.16) will likely work without issues, using 3.10.17 ensures exact reproducibility.
    *   You can download it from [python.org](https://www.python.org/downloads/release/python-31017/).
    *   Alternatively, using a Python version manager like `pyenv` (Linux/macOS) or `conda` is highly recommended to easily install and switch between specific Python versions. See Step 2 for how to check your installed version and command.
2.  **pip**: The Python package installer (usually comes bundled with Python).
3.  **Git**: (Optional, but likely needed to clone the repository).
4.  **This Repository**: You need a copy of this project's files, including the `requirements.txt` file (ensure you have created this file based on the packages used in the notebooks).
5.  **Jupyter Notebook, Jupyter Lab, or VS Code (with Python/Jupyter extensions)**: Required to run the `.ipynb` project files using the virtual environment created below.

## Setup Instructions

Follow these steps to create an isolated virtual environment and install the required packages.

1.  **Clone the Repository Using the SSH or HTTP key:**
    ```bash
    git clone git@github.com:112201019/POS-Tagging-NLP-Project.git
    cd POS-Tagging-NLP-Project
    ```

2.  **Find Your Python 3.10.17 (or compatible 3.10.x) Command:**
    Open your terminal. You need to identify the command used to execute your Python 3.10.17 installation (or a compatible 3.10.x version like 3.10.16). **Do not use the full version string `python3.10.17` as the command.** Try these possibilities until one reports the correct version:
    ```bash
    # Common commands to try:
    python3.10 --version
    python3 --version
    python --version
    # If using pyenv and 3.10.17 is set locally/globally:
    # python --version
    # If using conda and in an environment with 3.10.17:
    # python --version
    ```
    Make a note of the command that successfully reports `Python 3.10.17` we need it specifically to make the code run smoothly with no errors.

3.  **Create a Virtual Environment:**
    Navigate to the project's root directory (where `requirements.txt` is located). Create a virtual environment named `nlp_env` using the Python command you identified in Step 2.
    ```bash
    # --- IMPORTANT ---
    # Replace 'python3.10' below with the command that worked
    # for your Python 3.10.17 (or compatible) installation in Step 2.
    # Example: If 'python3.10' worked, use:
    # -----------------
    python3.10 -m venv nlp_env
    ```
    This creates an isolated environment in the `nlp_env` folder.

4.  **Activate the Virtual Environment:**
    You must activate the environment in your terminal session before installing packages or running the code.

    *   **On Linux or macOS (bash/zsh):**
        ```bash
        source nlp_env/bin/activate
        ```
    *   **On Windows (Command Prompt - `cmd.exe`):**
        ```bat
        .\nlp_env\Scripts\activate.bat
        ```
    *   **On Windows (PowerShell):**
        ```powershell
        .\nlp_env\Scripts\Activate.ps1
        ```
    Your terminal prompt should now be prefixed with `(nlp_env)`.

5.  **Install Dependencies:**
    With the virtual environment activated, install all required packages from the `requirements.txt` file:
    ```bash
    # Ensure ipykernel is included for Jupyter/VS Code integration
    pip install -r requirements.txt
    ```
    This may take a few minutes. *Note: Ensure your `requirements.txt` includes all necessary packages like `conllu`, `scikit-learn`, `sklearn_crfsuite`, `seaborn`, `matplotlib`, `torch`, `torchcrf`, `tensorflow`, `tensorflow_addons`, `transformers`, `datasets`, `tqdm`, `numpy`, `jupyter`, `ipykernel`.*

6.  **Verify Setup (Optional):**
    Confirm the correct Python version and packages are installed within the active environment:
    ```bash
    python --version
    # Expected Output: Python 3.10.17 (or your compatible version)

    pip list
    # Check if packages from requirements.txt are listed
    ```
7. select the kernel to this virtual environment created 

8. download the dataset repos and put them in the same folder as the .ipynb files
    1. UD_English-GUM: https://github.com/UniversalDependencies/UD_English-GUM
    2. UD_Telugu_English-TECT: https://github.com/UniversalDependencies/UD_Telugu_English-TECT
    
## Usage

The project code is primarily contained within Jupyter notebooks.

```bash
# Ensure your virtual environment is activated first!
# (Your prompt should show (.venv))

# 1. Launch Jupyter Lab or Jupyter Notebook (from the activated terminal):
jupyter lab
# or
jupyter notebook

# OR: Open the project folder in VS Code.

# 2. Open the relevant notebook file:
#    - For English POS Tagging (GUM dataset):
#      NLP-Project.ipynb
#    - For Telugu-English POS Tagging (TECT dataset):
#      NLP-Project-Telugu.ipynb

# 3. Select the Correct Kernel:
#    - In Jupyter Lab/Notebook: Go to Kernel -> Change Kernel -> Select "nlp_env".
#    - In VS Code: Click on the kernel indicator (usually bottom-right or top-right) and select the Python interpreter located within your `.venv` folder or the kernel named "Python (NLP Project)".

# 4. Run the cells within the chosen notebook sequentially.
#    This will execute the data loading, preprocessing, model training (if applicable),
#    evaluation, and display the results and visualizations using the packages
#    installed in your virtual environment.

# Note: Ensure the required datasets (UD_English-GUM/, UD_Telugu_English-TECT-master/)
# are placed correctly relative to the notebook files as expected by the code's paths.
```
## Known Bugs and/or Issues

We strive for perfection, but acknowledge there might be some rough edges. Here are issues we are currently aware of:

*   **Performance:** Processing very large input files (e.g., > 1GB) may be slow or consume significant memory. We are working on optimization strategies.
*   **Edge Case Handling:** The data validation routine might not catch all possible malformed input scenarios yet. Specifically, files with mixed encoding might cause unexpected errors.
*   **[If Applicable] UI Display:** On smaller screen resolutions, some elements in the web interface might overlap slightly.
*   **Compatibility:** While expected to work on major platforms (Linux, macOS, Windows), extensive testing has primarily been done on Linux (Ubuntu 22.04) and Python 3.10. Minor compatibility issues on other platforms might exist.

We track issues on our [**GitHub Issues page**](<Your-GitHub-Repo-Link>/issues) (Please add the actual link!). Please report any new bugs you find there.

## Troubleshooting

Encountering problems? Here are some common issues and their solutions:

*   **Problem:** `ModuleNotFoundError: No module named 'some_package'`
    *   **Solution:** Ensure your virtual environment is activated. Run `source .venv/bin/activate` (Linux/macOS) or `.\.venv\Scripts\activate` (Windows) in your terminal *before* running the Python script. Also, double-check that you installed all dependencies using `pip install -r requirements.txt` while the environment was active.

*   **Problem:** `FileNotFoundError: [Errno 2] No such file or directory: 'data/input.csv'`
    *   **Solution:** Verify that the specified file (`data/input.csv` in this example) exists and that you are running the script from the correct directory (usually the project's root folder). Relative paths depend on your current working directory. Check configuration files for correct path settings.

*   **Problem:** Installation fails for a specific package (e.g., a package requiring compilation).
    *   **Solution:** Ensure you have the necessary build tools installed on your system (like `gcc`, `python3-dev` on Debian/Ubuntu, or Build Tools for Visual Studio on Windows). Check the specific package's documentation for prerequisites. You might also try upgrading pip first: `pip install --upgrade pip`.

*   **Problem:** Incorrect output or unexpected behavior.
    *   **Solution:** Double-check your input data format against the expected format described in the documentation (or add this info if missing!). Verify any configuration settings or command-line arguments. If the problem persists, consider opening an issue with details.

*   **Problem:** [If Network Related] Connection errors or timeouts when contacting an external API.
    *   **Solution:** Check your internet connection. Ensure any required API keys or credentials are correctly set in your environment variables or configuration file. Verify that the external service is operational.

## Credits and Acknowledgments

This project was developed by:

*   Sriram Nangunoori (112201019@smail.iitpkd.ac.in / sriramnangunoori1@gmail.com)
*   Shrikant Tryambak Budde Reddy (142402010@smail.iitpkd.ac.in / shreebudde24@gmail.com)
*   Abhinay Gampa (142201013@smail.iitpkd.ac.in / abhinaygampa8@gmail.com)

We rely on several fantastic open-source libraries, including (but not limited to):

*   **`numpy`**: For fundamental numerical operations and array handling, especially when interfacing with deep learning frameworks.
*   **`pandas`**: Used for organizing and displaying evaluation metrics and error analysis results in tables.
*   **`conllu`**: For parsing the input datasets provided in the standard CoNLL-U format.
*   **`scikit-learn`**: For standard machine learning evaluation metrics (like `classification_report`, `confusion_matrix`, `accuracy_score`) and utilities like `KFold` cross-validation.
*   **`sklearn_crfsuite`**: For implementing and evaluating the Conditional Random Field (CRF) baseline model.
*   **`matplotlib` & `seaborn`**: For generating visualizations, such as confusion matrices and training history plots.
*   **`torch` & `torchcrf`**: Used for the PyTorch implementation of the BiLSTM-CRF model (core framework and CRF layer).
*   **`tensorflow` & `tensorflow_addons`**: Used for the TensorFlow implementation of the BiLSTM-CRF model (core framework and CRF layer via `tfa.text`) and the BERT model.
*   **`transformers` (Hugging Face)**: Crucial for providing pre-trained BERT models (`TFBertModel`) and the corresponding tokenizer (`BertTokenizer`) used in the fine-tuning approach. Also used for data collation (`DataCollatorForTokenClassification`).
*   **`datasets` (Hugging Face)**: Used to facilitate the conversion of Python data structures into TensorFlow datasets for use with the `transformers` library.
*   **`tqdm`**: For displaying visual progress bars during time-consuming operations like model training.

These libraries greatly simplified the implementation of data handling, model building, training, and evaluation. Ensure all these are listed in your `requirements.txt` file for proper environment setup.

## Acknowledgments

We would also like to acknowledge:

*   The creators and maintainers of the **Universal Dependencies (UD)** project, specifically the **UD_English-GUM** and **UD_Telugu_English-TECT** datasets, which were essential resources for training and evaluating our models.
*   The developers of the numerous open-source libraries and frameworks that formed the backbone of this project, including **Python**, **NumPy**, **Pandas**, **Scikit-learn**, **Matplotlib**, **Seaborn**, **`conllu`**, **`sklearn_crfsuite`**, **PyTorch**, **`torchcrf`**, **TensorFlow**, and **`tensorflow_addons`**.
*   The **Hugging Face** team and community for providing the invaluable `transformers` and `datasets` libraries, which greatly facilitated the use of pre-trained models like **BERT (`bert-base-cased`)**.
*   **Mr. Swapnil Hingmire** for providing valuable guidance and support throughout this NLP project.
*   The broader NLP research community and online platforms like Stack Overflow and library documentation for providing knowledge and solutions that aided our development process.

## Copyright and Licensing

Copyright (c) 2023 Sriram Nangunoori, Shrikant Tryambak Budde Reddy, Abhinay Gampa.

This project is licensed under the MIT License. See the `LICENSE` file for the full text.

## Contact Information

*   Sriram Nangunoori (112201019@smail.iitpkd.ac.in / sriramnangunoori1@gmail.com)
*   Shrikant Tryambak Budde Reddy (142402010@smail.iitpkd.ac.in / shreebudde24@gmail.com)
*   Abhinay Gampa (142201013@smail.iitpkd.ac.in / abhinaygampa8@gmail.com)
