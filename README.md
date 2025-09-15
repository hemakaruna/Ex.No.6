# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date: 12.09.2025  
# Register no. 212223060089  

---

## Aim
To develop a single Python function that can automatically read both `.csv` and `.json` files into a list of dictionaries, ensuring compatibility with multiple AI tools following the **Persona Pattern** approach.

---

## Apparatus Required
- Python **3.x**  
- Built-in libraries: `csv`, `json`, `os`  
- Sample dataset files:  
  - `examples/data.csv`  
  - `examples/data.json`  
- Text editor or IDE (**VS Code / PyCharm / Jupyter Notebook**)  

---

## Explanation
In AI and data-driven applications, different tools often require a **uniform input format**.  
The **Persona Pattern** emphasizes creating **adaptable, reusable functions** that act as a "persona" for different AI tools.  

Here, we create a single function `load_data()` that:

1. Accepts a **file path**  
2. Automatically **detects the file type** (`.csv` or `.json`)  
3. Converts the contents into a **list of dictionaries** format  
   - For `.csv`, each row becomes a dictionary using headers as keys  
   - For `.json`, the file is loaded directly into a list of dictionaries  
4. Returns standardized data for **AI models, pipelines, or analytics**

---

## Python Code

```python
import csv
import json
import os

def load_data(file_path):
    """
    Loads data from either a CSV or JSON file into a list of dictionaries.
    
    Args:
        file_path (str): Path to the file (.csv or .json)
    
    Returns:
        list[dict]: Data as list of dictionaries
    """
    if not os.path.exists(file_path):
        raise FileNotFoundError(f"{file_path} does not exist")

    extension = os.path.splitext(file_path)[1].lower()

    data = []
    if extension == ".csv":
        with open(file_path, mode="r", encoding="utf-8") as f:
            reader = csv.DictReader(f)
            data = [row for row in reader]

    elif extension == ".json":
        with open(file_path, mode="r", encoding="utf-8") as f:
            data = json.load(f)
            if isinstance(data, dict):
                data = [data]

    else:
        raise ValueError("Unsupported file format. Please use .csv or .json")

    return data


if __name__ == "__main__":
    csv_data = load_data("examples/data.csv")
    print("CSV Data:", csv_data)

    json_data = load_data("examples/data.json")
    print("JSON Data:", json_data)
```

# Conclusion:

  In this experiment, we successfully developed a single Python function that can automatically read both .csv and .json files and convert them into a standardized list of dictionaries. This ensures that multiple AI tools can seamlessly interact with the same dataset without requiring format-specific modifications. The experiment demonstrates the Persona Pattern, where the function acts as a common persona/interface for diverse AI applications, increasing reusability, adaptability, and efficiency in data-driven workflows.


<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/617d0cc1-af40-4cb0-9826-ff1b15c01d58" />



# Result: The corresponding Prompt is executed successfully.
