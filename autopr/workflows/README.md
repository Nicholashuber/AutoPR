

<!-- Living README Summary -->
## 🌳 Living Summary

This folder contains files related to workflows and actions for automating various tasks. The `__init__.py` file provides functions to collect and load workflows from YAML files. The `autogenerate_readmes.yaml` file contains workflows and actions for generating and updating README summaries for files and folders. The `insert_into_readme.yaml` file defines an action for inserting content into a file. The `summarize_pr.yaml` file defines a GitHub Actions workflow for summarizing changes in a pull request.


### `__init__.py`

📋 This file defines functions to collect and load workflows from YAML files.
📂 It recursively searches for YAML files in a given folder and its subfolders.
🔧 The `_collect_workflows` function collects workflows from a single YAML file.
🌐 The `_load_workflows_in_folder` function loads workflows from multiple YAML files in a folder.
📂 The `get_all_workflows` function is the main entry point, which loads both default and custom workflows.
📄 Default workflows are loaded from the same folder as this file.
🗂️ Custom workflows are loaded from a specified directory and its subfolders.
📥 The `config_dir` and `repo_path` parameters control the location of custom workflows.
📑 The `TopLevelWorkflowConfig` class represents the collection of workflows.
🔍 The file also includes some logging and error handling functionality.


### `autogenerate_readmes.yaml`

📋 This file contains a set of workflows and actions for generating and updating README summaries for files and folders. It is intended to automate the process of summarizing the contents of files and providing an overview of folder contents. The workflows include steps for reading files, summarizing files, summarizing folders, reformatting the results, and updating the README with the generated summaries.


### `insert_into_readme.yaml`

📝 This file defines an action called "insert_into_readme"
📂 The action inserts content into a file between two HTML-style comments
📄 If the file doesn't exist, it will be created
🔀 The content will be appended to the end of the file if two comments are not found
📥 Inputs include the filepath, tagname, and content to insert
🔁 The action involves reading the file, inserting the content between comments, and writing the file
✅ Outputs include the content of the file after the insertion and the success status of the write operation
🔧 The file can be customized to work with different file paths and content
⚠️ Empty outputs are commented out
📚 The purpose of the file is to define an action that can be used in a larger workflow.


### `summarize_pr.yaml`

📝 This file defines a GitHub Actions workflow called `summarize_pr`. 
📥 It takes a pull request as input and performs several steps to summarize the changes in the pull request.
💻 The first step uses a bash command to get the difference between the base commit and the pull request commit.
📄 The second step prompts the user to summarize the changes in the pull request using markdown and emojis.
📨 The user's response is stored in the `summary` variable.
💬 The final step adds a comment to the pull request with the summarized changes.


<!-- Living README Summary -->