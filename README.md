# ✅ Datasphere XLIFF Helper – Local Translation Automation Tool

A lightweight **Python–Flask** application that converts **SAP Datasphere XLIFF files** ↔ **Excel** and automates translations.
It eliminates manual copy/paste work and preserves the exact XLIFF structure.

---

## 🚀 Featured Tools

### ✔ Convert .xlf → .xlsx
* Extracts all `trans-unit` fields
* Auto-detects the **model name**
* Extracts the **target language** from filename (e.g., `MODEL_DE.xlf`)
* Generates Excel with columns: `id | source | target | lang | auto_translate_formula`

### ✔ Convert .xlsx → .xlf
* Preserves original XLF structure **exactly**
* Updates **only** the `<target>` tag for each field
* Produces a clean SAC-ready XLIFF file: `MODELNAME_LANG.xlf` (e.g., `AM_REPORTING_DE.xlf`)
---

## 🧩 Prerequisites

Please install:
* **Python 3.8+**
  ```
  https://www.python.org/downloads/windows/
  ```
  ```
  https://www.python.org/downloads/macos/
  ```
<details>
  <summary>
    💡 Troubleshooting: Checking and Updating Python Path (Windows & macOS)
  </summary>

### 💻 Checking Python Version in Terminal
To ensure Python is correctly installed and accessible from your terminal, run the following commands:

| OS | Command | Alternative |
| :--- | :--- | :--- |
| **Windows** | `python --version` | `py --version` |
| **macOS/Linux** | `python3 --version` | `python --version` |

If you receive a "command not found" error, you need to update the path.

---

### 🪟 Updating Path on Windows (if Python is not found)

If Python was not added to the PATH during installation, you must add the installation folder and its `Scripts` subfolder to the Windows Environment Variables.

1.  **Find your Python Path:** Locate the folder where `python.exe` is installed (e.g., `C:\Users\YourName\AppData\Local\Programs\Python\Python310`).
2.  Search the Windows Start Menu for **"Environment Variables"** and click **"Edit the system environment variables"**.
3.  In the **System Properties** window, click the **"Environment Variables..."** button.
4.  Under **"System variables"** or **"User variables"**, find and select the **`Path`** variable, then click **"Edit..."**. 
5.  Click **"New"** and add **two separate paths**:
    * The Python installation folder (e.g., `C:\Users\YourName\AppData\Local\Programs\Python\Python310`)
    * The Scripts subfolder (e.g., `C:\Users\YourName\AppData\Local\Programs\Python\Python310\Scripts`)
6.  Click **"OK"** on all windows to save the changes.
7.  **Close and reopen your terminal/VS Code** to apply the new path.

### 🍎 Updating Path on macOS (if Python is not found)

On macOS, you update the PATH by editing your shell's configuration file (usually `.zshrc` or `.bash_profile`).

1.  **Locate the Python executable path.** This might be in a path like `/Library/Frameworks/Python.framework/Versions/3.x/bin`.
2.  **Open your shell configuration file.** If you are on a modern Mac (macOS Catalina or later), the default shell is **Zsh**, so use the `.zshrc` file.
    ```bash
    nano ~/.zshrc
    # OR for older macOS:
    # nano ~/.bash_profile
    ```
3.  **Add the path.** Add the following line to the end of the file, replacing `<PYTHON_PATH>` with your actual path, and save it.
    ```bash
    export PATH="<PYTHON_PATH>:$PATH"
    ```
4.  **Apply the changes.** Run the `source` command to apply the changes without restarting the terminal.
    ```bash
    source ~/.zshrc
    # OR
    # source ~/.bash_profile
    ```
5.  **Verify.** Open a new Terminal window and run `python3 --version`.
</details>

---
## 📦 Installation

1.  Download the folder:
    * Navigate to the repository page on GitHub.
    * Above the list of files, click the green **`< > Code`** button.
    * In the dropdown that appears, click **`Download ZIP`**.

    <img width="250" height="250" alt="Screenshot 2025-12-12 123644" src="https://github.com/user-attachments/assets/d497f842-a19b-4e82-bd00-dd70e26cbbb1" />

    * Extract the contents to your preferred location. The resulting folder will be named:
    ```
    dsph_xliff_helper_python/
    ```
2.  Open the folder in an IDE - VS code:

    <img width="250" height="250" alt="Screenshot 2025-12-12 124118" src="https://github.com/user-attachments/assets/89b920cc-591b-4b0d-8dbd-cc415b714065" />

3.  Open terminal and Install dependencies:

     <img width="300" height="250" alt="image" src="https://github.com/user-attachments/assets/72cc4d0f-e344-4480-8290-061c818c2003" />

    ```bash
    pip install -r requirements.txt
    ```

5.  Start the application:
    ```bash
    python app.py
    ```
6.  Access the webpage hosted locally:
    ```url
    http://localhost:5000/
    ```
---

## 🔄 How to Use

### STEP 1 — Convert XLF → Excel
1.  **Download and Prepare the XLF File**
    * Download the translation `.xlf` file from the **SAP Datasphere** **Translation** tab based on your Analytical model.
    * **Crucial Naming Convention:** Ensure the file name follows this format: `<Modelname>_<SPRAS>.xlf` where `SPRAS` (language code) is **2 letters only**.
        * **Example:** `AM_MY_MODEL_DE.xlf` (Model: `AM_MY_MODEL`, Language: `DE`)
2.  **Upload the Prepared XLF file**
3.  Click **Convert**
    * A file is donwloaded: `<Model>.xlsx`

### STEP 2 — Convert Excel → XLF
1.  Fix the **excel formula in column E [auto_translate]** and **paste it as values to Column C [target]**, then Save the file.
2.  **Upload the Excel** you saved from previous step
3.  Click **Convert**
    * You receive the final Datasphere-ready file: `<Model>_DE.xlf`
---

## 📝 Logging

All events are logged in: `logs/app.log`
