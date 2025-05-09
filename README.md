# 🦊 FoxPy (.fpy) Script Runner & VS Code Plugin

This project lets you create and run `.fpy` scripts — a custom file format that combines **JSON metadata** and **Python code** in a single file. It includes:

- ✅ A Python runner for `.fpy` files
- ✅ A Visual Studio Code plugin to run `.fpy` scripts directly from the editor

---

## 🧠 What is `.fpy`?

A `.fpy` file contains:
- A JSON metadata block at the top (inside `/*json ... */`)
- Followed by Python code that can read and manipulate this metadata

### 📝 Example `.fpy` File

```python
/*json
{
  "author": "FoxDev",
  "version": "1.0",
  "target_file": "another.fpy",
  "update": { "version": "2.0", "author": "NewAuthor" }
}
*/

from fpy_runner import update_fpy_metadata

# Use metadata to update another .fpy file
update_fpy_metadata(__json__["target_file"], __json__["update"])
print("Updated metadata on target file.")
🔧 How to Use
1. 📦 Python Runner (CLI)
Install Python 3.8+ and run any .fpy file from the terminal:

bash
Copy
Edit
python fpy_runner.py path/to/your_file.fpy
The runner will:

Parse the JSON block

Execute the Python code with metadata available as __json__

Support built-in update_fpy_metadata() function

2. 🧩 VS Code Plugin
Run .fpy scripts directly inside Visual Studio Code.

🔌 Install Manually:
Clone this repo or download the folder

Open it in VS Code

Press F5 to run in Extension Development Mode

Open any .fpy file

Use Ctrl+Shift+P → Run FPY File

🏃 Output Example
When you run a .fpy file, it will:

Execute your embedded Python code

Display stdout or error in a popup

Modify any file metadata as written in the script

⚙️ Project Structure
bash
Copy
Edit
.vscode-fpy/
├── extension.js        # VS Code plugin logic (calls Python)
├── package.json        # VS Code extension manifest
├── fpy_runner.py       # Python runner for .fpy files
🔐 Security Warning
Since .fpy files run Python directly, they can execute arbitrary code.

Only run .fpy files from trusted sources!

🛠 Features Planned
 Syntax highlighting for .fpy

 File icon for .fpy files in VS Code

 Command-line metadata injector

 Self-modifying .fpy scripts

🤝 Contributing
Pull requests welcome! Feel free to open issues, suggest features, or improve the runner and VS Code integration.

