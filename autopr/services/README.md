

<!-- Living README Summary -->
## 🌳 Living Summary

This folder contains several Python files that implement various services and functionalities for managing and automating actions in a pull request workflow. The files include implementations for services such as caching, committing changes, applying diffs, interacting with a platform (e.g., GitHub), publishing updates to pull request descriptions, and executing workflows. Each file provides a specific set of functionalities and is designed to work together to create a comprehensive automated pull request workflow system.


### `__init__.py`

📄 This file is empty.


### `action_service.py`

📝 This file contains the implementation of the `ActionService` class, which is responsible for managing and running actions in an automated pull request workflow. 
📋 It provides methods to find and instantiate actions, get action inputs, and run actions either sequentially or iteratively. 
📦 The class relies on other classes and modules for caching, publishing, and interacting with the repository and platform services. 
💧 Actions are represented as subclasses of the `Action` base class and are loaded from the `autopr/actions` directory. 
🔍 The `get_action_inputs` method resolves and validates input values for an action, taking into account prompt contexts and variable declarations. 
⚙️ The `_instantiate_and_run_action` method creates an instance of an action, publishes the inputs, and executes the action's `run` method. 
📝 The `run_action` method runs a single action, while the `run_action_iteratively` method iterates over a list or a specified number of times and runs the action for each iteration. 
📄 The outputs of the actions are published and the resulting new variables are extracted and returned as a `ContextDict`. 
🔁 Error handling is implemented to log and publish any exceptions that occur during the execution of an action.


### `cache_service.py`

📂 This file defines a `CacheService` class and a `ShelveCacheService` class.    
💾 The `CacheService` class is an abstract base class that defines the interface for storing and retrieving data from a cache.    
🔗 The `ShelveCacheService` class is a concrete implementation of the `CacheService` class that uses the `shelve` module to store data in a file-based cache.    
📁 The `ShelveCacheService` class takes a configuration directory and an action ID as input.    
📝 The `store` method in the `ShelveCacheService` class stores a key-value pair in the cache, with an optional namespace.    
🔍 The `retrieve` method in the `ShelveCacheService` class retrieves the value associated with a given key from the cache, with an optional namespace.    
📂 The cache data is stored in a file in the specified configuration directory, with the namespace as part of the file name.    
⚙️ The cache file is created if it does not exist, and the cache is persisted to disk when the shelf is closed.    
🔒 The `store` and `retrieve` methods use the default namespace if no namespace is provided.


### `commit_service.py`

📝 This file contains a class called `CommitService` which is a service for managing commits in a Git repository.
🚀 The purpose of this service is to create branches, commit changes, and push the commits to the repository.
🌱 It ensures that there is always a commit on the branch.
📁 The service takes the repository, repository path, branch name, and base branch name as parameters in its constructor.
🔀 The `overwrite_new_branch` method creates a new branch by checking out the base branch, pulling the latest changes, deleting any existing branch with the same name, and creating a new branch with the same name from the base branch.
✅ The new branch is then checked out, and an empty commit is created.
🔄 The `ensure_branch_exists` method checks if the branch already exists. If it does, it checks out the branch and pulls the latest changes. If it doesn't exist, it calls the `overwrite_new_branch` method to create a new branch.
📝 The `commit` method is used to add and commit changes to the branch. It also handles removing an empty commit if it exists and pushes the branch to the remote repository.
🔧 The class uses the `git` module from the `git` library and a custom logger for logging messages.


### `diff_service.py`

📝 This file contains three classes: `DiffService`, `GitApplyService`, and `PatchService`.
🔍 The `DiffService` class is responsible for getting and applying diffs.
🔄 Diffs are represented as `DiffStr`, which is an alias for `str`.
⚙️ The `apply_diff` method in `DiffService` raises a `NotImplementedError`.
📥 The `get_diff` method in `DiffService` gets the diff of the staged files in the repository.
📝 The `GitApplyService` class extends `DiffService` and applies the diff using the `git apply` command.
🌈 The `PatchService` class also extends `DiffService` and applies the diff using the `patch` command.
🔒 Both `GitApplyService` and `PatchService` write the diff to a temporary file before applying it.
📝 The purpose of this file is to provide services for getting and applying diffs in a Git repository.


### `platform_service.py`

📝 This file contains the implementation of two classes: `PlatformService` and `GitHubPlatformService`. 
🤖 `PlatformService` is a base class for making API calls to a platform, such as GitHub. It defines several methods for interacting with the platform, such as publishing comments, creating pull requests, and updating pull request bodies and titles.
🐙 `GitHubPlatformService` is a subclass of `PlatformService` specifically designed for interacting with the GitHub platform. It implements the methods defined in `PlatformService` using the GitHub API. It also provides additional functionality, such as finding existing pull requests and setting the draft status of a pull request.
🔒 The `GitHubPlatformService` class requires a GitHub access token to authenticate API requests.
🔧 There is also a `DummyPlatformService` class, which is a dummy implementation of `PlatformService` that does not perform any actual API calls. It can be used for testing or as a placeholder when a real platform service is not available.
📚 The file also defines several data classes for representing issues, pull requests, and events. These classes are used as return types or parameters for some of the methods in the `PlatformService` and `GitHubPlatformService` classes.
❗️ Some methods in the `PlatformService` and `GitHubPlatformService` classes are marked as `NotImplementedError`, indicating that they need to be implemented in subclasses.
🔑 The `GitHubPlatformService` class uses the `aiohttp` library for making asynchronous HTTP requests to the GitHub API.
🚧 The `GitHubPlatformService` class includes some error handling and logging functionality for handling failed API requests.
📖 The file also includes a `parse_event` method in the `GitHubPlatformService` class for parsing events received from the GitHub platform. This method returns an object representing the parsed event.


### `publish_service.py`

📄 This file contains the implementation of a service called `PublishService` and its subclasses `GitHubPublishService` and `DummyPublishService`. 
🔧 The purpose of this service is to publish updates and progress to the pull request description on a platform, such as GitHub. 
📝 It provides methods to publish text updates, code blocks, and sections to the pull request description. 
🔄 The service can schedule updates asynchronously and automatically update the pull request description with the latest progress. 
📝 The `GitHubPublishService` subclass adds additional functionality specific to GitHub, such as adding a shield linking to the action logs and a "Fixes #{issue_number}" link. 
🐛 If an error occurs during the publishing process, an error report can be generated and a new issue can be opened to report the error. 
⚙️ The `DummyPublishService` subclass is a dummy implementation used for testing or as a placeholder when the actual platform service is not available. 
🔐 The service supports setting the pull request title, body, and draft status. 
🔀 It also provides methods to start and end sections, update section titles, and publish updates and code blocks within sections.


### `utils.py`

📝 This file contains functions for formatting Python objects for publishing. 
🔍 The `truncate_strings` function truncates long strings and dictionaries/lists containing long strings, adding an ellipsis to indicate truncation. 
🔍 The `nested_to_dict` function converts nested objects (dictionaries and lists) into regular dictionaries. 
🔍 The `format_for_publishing` function formats the object for publishing by converting it to a dictionary, truncating strings, and dumping it to JSON with indentation. 
🔄 The file uses the `pydantic` library for working with data validation and serialization.


### `workflow_service.py`

📝 This file defines a class called `WorkflowService` that provides functionality for executing workflows. 
🧩 It handles triggers, events, and the execution of actions and workflows.
🌊 It can invoke workflows either directly or iteratively.
📣 Triggers can be used to start the execution of workflows based on events.
🎬 It supports the passing of inputs and capturing of outputs for workflows.
📚 It provides methods for validating inputs and outputs of workflows.
🏁 The `execute_workflow` method executes the steps of a workflow in order.
🚀 The `execute` method handles the execution of various types of executables such as actions, workflows, and context actions.
🔧 It also includes some utility methods for getting the name of an executable and preparing workflow inputs.

<!-- Living README Summary -->