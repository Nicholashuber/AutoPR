<div align="center">

# 🌳 AutoPR 🌳

[![Discord](https://badgen.net/badge/icon/discord?icon=nope&label&color=purple)](https://discord.gg/ykk7Znt3K6)
[![Docs](https://badgen.net/badge/icon/docs?icon=docs&label&color=blue)](https://docs.autopr.com)

Breathe life into your codebase, configurably  

</div>

## 🌟 Features

📄 Summarize changes by adding a "summarize" label to a PR  
🌳 Living summaries of your code in nested READMEs

... more coming soon!

## 🚀 Getting Started

Please see the [installation guide](https://docs.autopr.com/installing/github).

## 🐞 Known Bugs

We're pre-alpha, so expect bugs. Here are some known ones:

- Caching is not working properly, so living summaries get regenerated on every push.

See below for an example of AutoPR's README summary:

<!-- Living README Summary -->
## 🌳 Living Summary

This folder contains files and folders related to an automation framework for managing and automating actions on GitHub. The "Dockerfile" is used to build a Docker image for a Python project. The "LICENSE.md" file contains the MIT License for the software. The "Makefile" defines tasks for a Python project, such as type checking and running tests. The "action.yml" file is a configuration file for an automated process called "Automatic Pull Request". The "autopr" folder contains Python files and folders that implement various functionalities for the automation framework. The "entrypoint.sh" file is a shell script that sets up global configurations and runs the automation framework. The "poetry.lock" and "pyproject.toml" files are configuration files for the Python project. There are also JSON schema files that define the structure and properties of workflow definitions and strict workflow models.


### `Dockerfile`

📋 This file is a Dockerfile used to build a Docker image for a Python project.   
🔧 It installs git and sets up an entrypoint.   
📦 It copies the project's `pyproject.toml` and `poetry.lock` files.   
🔍 It installs the project's dependencies using Poetry.   
📂 It sets the working directory to `/app` and copies the entire project.   
🔧 It installs the application.   
🏃‍♀️ It sets the command to run the application using the `entrypoint.sh` script.


### `LICENSE.md`

💼 This file contains the MIT License for the software.
💡 The purpose of the file is to grant permission to use, modify, and distribute the software.
📝 The license includes conditions that must be followed.
📋 The license also includes a warranty disclaimer.
👥 The copyright holder is Raphael Francis Ltd.
📅 The license is effective from 2023 onwards.
📄 The license should be included in all copies or substantial portions of the software.


### `Makefile`

📄 This file defines tasks for a Python project   
🔍 It includes tasks for type checking, running tests, and generating a schema  
🔧 The `type` task uses `pyright` for type checking  
🧪 The `test` task runs tests using `pytest` in the `autopr/tests` directory  
📋 The `schema` task generates a schema using the `autopr.models.config.entrypoints` module  
🔀 The `all` task runs all the defined tasks (`type`, `test`, and `schema`)  
💡 This file can be used to manage the development and testing workflow  



### `action.yml`

📝 This file is a configuration file for an automated process called "Automatic Pull Request".
🔧 It specifies the details and settings for running the process.
🐳 The process runs using Docker, with a specified Docker image.
🎨 It includes branding elements such as an icon and color.
🔑 The process requires a GitHub token as an input.
🌱 It has default values for inputs like base branch, loading GIF URL, target branch name template, and overwrite existing flag.
💻 The purpose of the process is to generate pull requests automatically based on issues.
🌐 It includes a default loading GIF URL to display while the PR is being generated.
🔄 The target branch name is generated using a template, including the issue number.
🔧 The overwrite_existing flag determines whether existing branches and pull requests should be overwritten.


### `autopr`

This folder contains a collection of Python files and folders that implement various functionalities for an automation framework. The "actions" folder contains Python files that define actions such as running commands, publishing comments, and generating strings. The "gh_actions_entrypoint.py" file serves as an entry point for a GitHub Actions workflow. The "log_config.py" file provides logging configuration settings. The "main.py" file implements the main service for the automation framework. The "models" folder contains files defining Pydantic models. The "services" folder contains files implementing various services for managing and automating actions. The "triggers.py" file provides a way to retrieve triggers defined in a repository. The "workflows" folder contains files related to automating tasks with workflows and actions.


### `entrypoint.sh`

📝 This file is a shell script.
🔧 It sets a global configuration for git, including a safe directory and user email/name.
🔌 It activates a virtual environment.
🐍 It runs a Python module called `autopr.gh_actions_entrypoint`.


### `poetry.lock`

📄 This file is an executive summary of the project.     
📝 It provides a high-level overview of the project goals and objectives.     
📊 It includes key metrics and performance indicators.     
🔍 It summarizes the main findings and recommendations.     
🗓️ It outlines the project timeline and milestones.     
💼 It highlights the project team and their roles.     
🌐 It discusses any potential risks or challenges.     
📢 It identifies key stakeholders and their involvement.     
💡 It serves as a guide for decision-making and planning.     
✅ It ensures a common understanding of the project's purpose.    


### `pyproject.toml`

📝 The file is a configuration file for a Python project.  
📦 It uses Poetry as the package manager.  
📚 It specifies the project name, version, and description.  
👥 It lists the authors and the license of the project.  
📄 The readme file is specified as "README.md".  
📦 It includes the "autopr" package in the project.  
🔗 It lists the dependencies for the project, including Python, Pydantic, GitPython, and others.  
🧪 It specifies test dependencies, such as Pytest and Aioresponses.  
🔧 It sets up the build system using Poetry.  
🔍 It configures Pyright for type checking and linting.


### `strict_workflow_schema.json`

📋 This file is a JSON schema definition for a strict workflow model.
🔄 It defines various action models and their properties.
🔣 The action models include comment, set_issue_title, crawl_folder, bash, commit_and_push, write_into_file, insert_content_into_text, prompt, and read_file.
🔄 The action models can be used in a workflow definition to create a sequence of actions.
🔄 The workflow definition includes steps that can be either action models or other workflow invocations.
⚙️ The workflow definition can have inputs and outputs.
🔄 The workflow definition can also have conditional branches using IfLambda, IfExistsContext, and IfContextNotExists.
📚 The file also includes definitions for various data types used in the action models and workflow definition.
🔀 The file can be used to validate and define strict workflows for automation or other purposes.


### `trigger_schema.json`

📋 This file is a JSON schema definition for a configuration file.
🔗 It defines various models and templates for different actions that can be performed in a workflow.
🔀 The file includes definitions for actions like commenting on an issue, crawling a folder, executing a bash command, and more.
📝 It also defines triggers like push triggers, label triggers, and comment triggers.
📂 Each action and trigger has its own set of inputs and outputs.
🔄 The purpose of this file is to provide a standardized schema for configuring workflows and actions in a system.
🔧 It allows users to define their workflow and actions by referencing the predefined models and templates.
💡 The file can be used to validate and generate configuration files for a workflow system.
📚 It serves as a documentation for the available actions, triggers, and their properties.
🛠️ Developers can use this file as a reference to implement the corresponding functionality in their workflow system.


### `workflow_schema.json`

💡 This file is a JSON schema that defines the structure and properties of a workflow definition.
💡 It describes various types of actions that can be performed within a workflow.
💡 Each action has its own set of inputs and outputs.
💡 The schema also includes definitions for different types of declarations and lambdas used within the actions.
💡 The workflow definition consists of a name, description, inputs, outputs, and a sequence of steps.
💡 Steps can be actions, workflow invocations, or conditional statements.
💡 Actions include commenting, setting issue titles, crawling folders, running bash commands, committing and pushing changes, writing into files, inserting content into text, prompting for input, and reading files.
💡 Workflow invocations can be either regular or iterable, depending on whether they are executed once or multiple times.
💡 Conditional statements allow for branching based on the evaluation of a lambda expression or the presence of a context variable.
💡 The schema provides a comprehensive structure for defining and executing workflows with various actions and logic.

<!-- Living README Summary -->