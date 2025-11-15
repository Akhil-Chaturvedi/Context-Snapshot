# Context-Snapshot
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Python: 3.6+](https://img.shields.io/badge/Python-3.6%2B-blue.svg)](https://www.python.org/downloads/)
[![Platform: Windows | macOS | Linux](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey.svg)](https://www.python.org/)

A powerful CLI tool to generate a complete snapshot of your project, including the directory tree and all file contents, into a single file for AI context.

## Why Use Context-Snapshot?
In the age of AI-assisted development, providing Large Language Models (LLMs) like ChatGPT, Gemini, or Claude with the full context of a project is crucial for getting accurate, relevant responses. Manually copying and pasting individual files is slow, incomplete, and unsustainable for large projects.

**Context-Snapshot** bridges this gap. It walks through your entire project, intelligently bundles all relevant source code into a single, well-formatted text file, and prepares it for easy pasting into any AI chat interface.

## Key Features
-   **Complete Project Snapshot:** Generates a detailed directory tree followed by the full contents of every included file.
-   **Intelligent File Exclusion:**
    -   Use a `.contextignore` file (with a syntax just like `.gitignore`) for precise control over what to exclude.
    -   If no `.contextignore` is found, choose from built-in presets for Python, Node.js, and Android projects.
-   **Smart Content Handling:**
    -   Automatically detects and skips binary files (images, executables, etc.).
    -   Consolidates directories containing *only* binary files into a single, clean "skipped" message in the output.
-   **Cross-Platform:** Written in standard Python, it works flawlessly on Windows, macOS, and Linux.
-   **`.gitignore` Integration:** Can automatically add its own generated files (`project_context.txt`, `.contextignore`) to your project's `.gitignore` to keep your repository clean.
-   **Zero Dependencies:** Runs out-of-the-box with a standard Python installation. No `pip install` required.

## Installation
Since this is a standalone script with no external dependencies, installation is as simple as cloning the repository.

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/Akhil-Chaturvedi/Context-Snapshot.git
    ```

2.  **Navigate into the directory:**
    ```sh
    cd Context-Snapshot
    ```

That's it! You're ready to go.

## Usage
1.  Run the script from your terminal:
    ```sh
    python context_snapshot.py
    ```
2.  The script will prompt you to enter the full path of the project folder you want to map.
    ```
    --- Context Snapshot Generator ---
    Enter the full path of the folder to map: C:\Users\YourUser\Projects\my-cool-project
    ```
3.  Follow the on-screen prompts to configure exclusions if a `.contextignore` file is not found.
4.  Once finished, a `project_context.txt` file will be created in the root of the target folder. You can now open this file, copy its entire contents, and paste it into your AI assistant's prompt.

## Configuration: The `.contextignore` File
The best way to control the output is by creating a `.contextignore` file in the root of the project you are analyzing. The syntax is identical to `.gitignore`.

-   Each line represents a pattern to ignore.
-   Lines starting with `#` are comments.
-   Use `*` as a wildcard.
-   End a pattern with `/` to specify a directory.

### Example `.contextignore`
```
# Ignore IDE and OS-specific files
.idea/
.vscode/
*.DS_Store
Thumbs.db

# Ignore dependency folders
node_modules/
venv/
.venv/

# Ignore build artifacts
dist/
build/
*.pyc

# Ignore specific files by name
local_secrets.json

# Ignore all log files in a specific directory
logs/*.log

# Exclude a specific file
app/src/main/res/raw/some_asset.xml
C:\Users\YourUser\Projects\my-android-project\app\src\main\res\raw\some_asset.xml
```

## Example Output
Given a simple project structure, the `project_context.txt` file will look like this:

```
# Context Snapshot Version: 1.0

PROJECT FILE MAP:
=================
Root: /path/to/my-cool-project
├─ .contextignore [skipped]
├─ data/
│   └─ user_data.dat
├─ main.py
├─ project_context.txt [skipped]
└─ venv/ [skipped]
==============
FILE CONTENTS:
-------
FILE: data/user_data.dat
-------
[Binary file skipped]
-------
FILE: main.py
-------
# main.py
def hello_world():
    print("Hello from Context-Snapshot!")

if __name__ == "__main__":
    hello_world()
```

## Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/Akhil-Chaturvedi/Context-Snapshot/issues).

## License
This project is licensed under the **GNU General Public License v3.0**. See the [LICENSE](LICENSE) file for details.
