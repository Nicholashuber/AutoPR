

<!-- Living README Summary -->
## 🌳 Living Summary

This folder contains a collection of Python files that implement various actions for an automation framework. These actions include tasks such as running bash commands, publishing comments on GitHub issues, committing and pushing changes to a remote repository, crawling folders to list their contents, inserting content into text at specified delimiters, generating strings using OpenAI's GPT-3 model, reading file contents, setting the title of an issue, and writing content into a file. The files use libraries such as Pydantic for input validation and modeling, and they are well-documented with comments and type hints.


### `__init__.py`

📁 The file imports modules and directories in the current directory.
🔎 It collects the names of Python files and directories without '__init__.py' in the current directory.
📚 The collected names are stored in '__all__' for potential usage.
📂 The file also imports all modules from the current directory.
🧩 It serves as a way to easily import all modules and directories in the current directory.



### `base.py`

📝 This file defines a base class for actions used in an autonomous agent. Actions are responsible for performing a single task, affecting the environment, and returning a result. 
🔒 The file also includes a metaclass for registering actions in a global registry.
🔑 The base class includes attributes for the ID, name, and description of an action.
🏃‍♂️ The base class has a `run` method that needs to be implemented by subclasses to execute the action.
🔧 The base class also has an initialization method that sets up various services and dependencies for the action.
📜 The file defines two type variables, `Inputs` and `Outputs`, which are used to specify the input and output types of an action.
📁 The file includes a function that returns a dictionary of all registered actions.
⚠️ The file has some error handling for duplicate action IDs and missing input/output type arguments.
🔍 The file imports various modules and types used by the action classes.
📚 The file includes some documentation and comments to explain the purpose and usage of the code.


### `bash.py`

📄 This file defines a class called "Bash" that is responsible for running a bash command and returning its output.
🎯 The purpose of this file is to provide a reusable action that can be used in an automation framework.
⚙️ The "Bash" class takes a command as input and uses asyncio to run the command in a subprocess.
📥 The input command is specified through the "BashInputs" class.
📤 The output of the command is captured and returned as a string through the "BashOutputs" class.
🔀 The file also includes a main block that demonstrates how to manually run the "Bash" action with a sample input.
📝 The file uses the pydantic library for input and output validation.
🧪 The file imports a utility function called "run_action_manually" for testing purposes.
🔗 The "Bash" class extends a base class called "Action" which provides a generic structure for actions in the automation framework.


### `comment.py`

📄 The file contains a class `Comment` that represents an action to publish a comment on a GitHub issue.
📝 The class has an `id` attribute that identifies it as the "comment" action.
🔗 The class has a `run` method that takes inputs and publishes the comment using a publish service.
🔧 The inputs for the `run` method include a comment string and an optional issue number.
📦 The class imports necessary modules and uses a base class for the action.
🔄 The `run` method is async and awaits the publishing of the comment.
💡 The file uses Pydantic for input validation and type checking.
📚 The purpose of the file is to provide functionality for publishing comments on GitHub issues.
⚙️ The file can be used as a part of a larger automation system or workflow.
💬 The file can be extended or customized to add more actions related to GitHub issues.


### `commit_and_push.py`

📄 This file defines a class called "CommitAndPush"   
📝 The purpose of this class is to commit and push changes to a remote repository   
🔒 It inherits from the "Action" class   
🎯 The "run" method is used to execute the commit and push action   
📝 The "run" method takes an "Inputs" object as input   
✏️ The "Inputs" object defines the commit message and optional filepaths   
🔑 The class has a unique identifier called "id"   
💻 The "commit_service" object is used to perform the commit and push   
🔒 The "run" method is asynchronous   
🤖 The default commit message is "AutoPR commit"


### `crawl_folder.py`

📄 This file defines a Python class called "CrawlFolder" that lists all the files and subfolders in a given folder, excluding certain files and directories.
📂 The purpose of this class is to crawl a folder and provide a list of its contents, which can be useful for various file management tasks.
🔍 It uses regular expressions to define patterns for files and directories that should be ignored during the crawl.
🔧 The class has a method to check if a file is binary or not, and it can optionally ignore binary files based on a flag.
📝 The class has input and output models defined using Pydantic, which specify the expected structure of the inputs and outputs.
📚 The input model allows specifying files and subfolders to ignore during the crawl, as well as the folder path to crawl.
💡 The class is designed to be used as an action in a larger system or application, as indicated by the inheritance from the "Action" base class.
🔨 The "run" method of the class performs the actual crawl and returns the list of file entries that passed the exclusion criteria.
⚙️ The code at the bottom of the file demonstrates how to manually run the "CrawlFolder" action using the provided inputs.


### `insert_content_into_text.py`

📄 This file contains a Python script that defines a class called `InsertContentIntoText`.
🔍 The purpose of this class is to insert content into a string at a specified delimiter.
🧩 The class has a method called `insert_tag_content_into_string` which performs the insertion logic.
🔧 The class also has a `run` method that takes inputs, calls the insertion method, and returns the modified content.
📝 The inputs include the existing content, delimiter, and the content to be inserted.
📥 The `run` method returns the modified content as an output.
⚙️ The file also includes an example usage of the `InsertContentIntoText` class.
🚀 The example demonstrates how to insert content when there are no delimiters and when there are two delimiters.
🔬 The file can be run directly to test the functionality of the class.


### `prompt.py`

📝 This file contains a Python script for generating a string using OpenAI's GPT-3 model.
🔧 It defines a class called "PromptString" that implements the functionality.
🔍 The class takes various inputs such as the model to use, prompt context, instructions, and prompt text.
🧩 It provides a method to trim the prompt context to fit within a specified token limit.
🔁 The class uses the Tenacity library for retrying API calls in case of errors.
📥 The "run" method invokes the OpenAI API to generate the string based on the inputs.
💾 The generated string is cached to avoid redundant API calls.
📄 The file also includes a test case for manually running the action.
🏃‍♀️ When executed as a standalone script, the test case is run using asyncio.


### `read_file.py`

📝 This file contains a Python class called "ReadFile" that represents an action to read the contents of a file. 
🔍 It uses the "pydantic" library for data validation and modeling. 
📂 The class has two nested classes called "Inputs" and "Outputs" that define the expected input and output data structures. 
📚 The "load_jupyter_notebook" method is used to read the contents of a Jupyter Notebook file, while the "ensure_file_exists" method ensures that a file exists at the given path. 
🔧 The "run" method is the main entry point of the class and it reads the contents of a file based on the provided inputs. 
🚀 The file can be run directly to test the "ReadFile" action with a sample input. 
💻 The file also includes an import statement and a conditional block for running the action manually. 
❌ If an error occurs during file reading, an error message is logged and the exception is re-raised. 
🧹 The file also includes a cleanup step to remove the temporary file created during testing.


### `set_issue_title.py`

📄 This file contains a class called SetIssueTitle that represents an action to set the title of an issue.   
🔧 The action is part of a larger system called autopr.   
🔑 The action has an id of "set_issue_title".   
📥 The action expects an input of type Inputs, which has a single attribute called title.   
🏃‍♀️ The action's run method is asynchronous and sets the title using a publish_service.   
💡 The file uses pydantic for input validation.   
⚙️ The file imports the BaseModel class from pydantic and the Action class from autopr.actions.base.   
📚 The purpose of this file is to define the behavior of the SetIssueTitle action.   
🔧 The file is likely part of a larger codebase that includes other actions and functionality.   
📝 The file is well-documented with comments and type hints.


### `utils`

This folder contains a file called `prompt_context.py` which implements a prompt context model and its configuration representation. The purpose of this file is to provide a structured representation of prompt context and its configuration for use in an automated prompt generation system. The file includes classes for mapping context variables, transforming configurations, and utility functions for string manipulation.


### `write_into_file.py`

📝 This file contains a Python script that implements an action called "WriteIntoFile".
🖋️ The purpose of this action is to write content into a file.
📥 It takes inputs such as the filepath, content to insert, and whether to append or replace the file content.
✏️ The action uses the "open" function to open the file in append or write mode, and writes the content into it.
📤 It returns an output indicating whether the file was written to successfully.
🧪 The script includes a test scenario where the action is manually run with sample inputs.
🔒 The file is deleted after the test is completed.
🔽 The action is defined as a subclass of the "Action" class from the "autopr.actions.base" module.
🔧 The "pydantic" library is used for data validation using the "BaseModel" class.
🔒 The script can be executed directly if it is the main module.

<!-- Living README Summary -->