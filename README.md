import nbformat

# Path to the uploaded notebook
notebook_path = "/mnt/data/InsuranceCostPrediction.ipynb"

# Load the notebook
with open(notebook_path, "r", encoding="utf-8") as f:
    notebook = nbformat.read(f, as_version=4)

# Extract code and markdown cells
code_cells = []
markdown_cells = []
for cell in notebook.cells:
    if cell.cell_type == "code":
        code_cells.append(cell.source)
    elif cell.cell_type == "markdown":
        markdown_cells.append(cell.source)

# Extract the first few markdown cells for project description
project_description = "\n".join(markdown_cells[:3])  # Taking first 3 markdown cells as description

# Extract first few lines of code for dependency analysis
sample_code = "\n".join(code_cells[:3])  # Taking first 3 code cells for reference

project_description[:500], sample_code[:500]  # Show initial content for analysis
