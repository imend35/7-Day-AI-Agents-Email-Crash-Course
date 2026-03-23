
## Day 1: Data Ingestion and Processing

On the first day, the goal was to build a pipeline to download and parse documentation from any GitHub repository.

### Key Learning & Tasks:
- **Environment Setup:** Used `uv` as a lightning-fast package manager to handle dependencies.
- **IDE Choice:** Instead of the standard Jupyter Notebook interface, I used **VS Code** with the **Jupyter Extension** and `ipykernel` for a more robust development environment.
- **Data Ingestion:** Implemented a memory-efficient way to download repositories as ZIP archives using `requests` and `zipfile`.
- **Parsing:** Extracted structured metadata (Frontmatter) and Markdown content using the `python-frontmatter` library.

### Technical Stack:
- **Language:** Python 3.10+
- **Manager:** uv
- **Environment:** VS Code (Jupyter Mode)
- **Libraries:** `requests`, `python-frontmatter`, `zipfile`, `io`

### Results:
Successfully processed the **FastAPI** repository:
- **Total documents processed:** 1554+ files
- **Data structure:** Each file is stored as a dictionary containing `filename`, `metadata`, and `content`.

---
🚀 Step-by-Step Project Implementation (Day 1)
I followed these exact steps to build the data ingestion pipeline for my AI Agent project.

Step 1: Environment Setup
First, I prepared a clean development environment using uv as my package manager. I chose VS Code over the standard Jupyter Notebook interface for a better coding experience.

Action: Created the project folder structure.

Terminal Commands:
Bash
mkdir aihero
cd aihero/project

uv init

uv add requests python-frontmatter ipykernel

uv sync

<img width="1059" height="522" alt="image" src="https://github.com/user-attachments/assets/73f9d866-a0cb-49d6-8366-7bcf5af9dd02" />
<img width="633" height="590" alt="image" src="https://github.com/user-attachments/assets/5b19e12e-b6b4-4c96-9cd3-135cc9e3e540" />

Step 2: VS Code & Kernel Configuration
Since I am using VS Code, I had to ensure that my notebook was using the correct virtual environment created by uv.

Action: Created a day1.ipynb file.

Action: Selected the Python interpreter located in .venv/Scripts/python.exe to avoid "ModuleNotFoundError" and ensure all libraries were accessible.

Step 3: Developing the Ingestion Code

I wrote a robust Python function to download any GitHub repository's documentation without saving it to the disk (In-memory processing).

Action: Used requests to fetch the ZIP archive from GitHub.

Action: Used zipfile and io to read the archive in RAM.

Action: Used python-frontmatter to separate the metadata (YAML) from the actual Markdown content.

Code : 

<img width="1044" height="859" alt="image" src="https://github.com/user-attachments/assets/7cab8487-fb6b-4de6-aee7-ef6ed6c5edbf" />

<img width="1003" height="202" alt="image" src="https://github.com/user-attachments/assets/81b15742-d6ae-4586-943a-14b3d008a46e" />

Step 4: Verification & Results

I tested the pipeline with the FastAPI repository to see if it could handle a large-scale project.

Result: Successfully processed 1554 documentation files.

<img width="545" height="72" alt="image" src="https://github.com/user-attachments/assets/de74c9c1-1091-46f0-bc97-70ea7259987c" />


