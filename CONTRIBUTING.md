# Contributing to AlluOS

We're thrilled you're interested in contributing to AlluOS! As a learning project and sandbox CLI, AlluOS thrives on community contributions. Whether you're fixing a bug, adding a new feature, improving documentation, or creating a new module, every contribution helps make AlluOS better.

This document outlines the guidelines for contributing to AlluOS.

---

## Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project, you agree to abide by its terms.

---

## Ways to Contribute

There are many ways you can contribute to AlluOS:

### 1. Report Bugs

* If you find a bug, please check the [GitHub Issues page](https://github.com/Kiwi8474/AlluOS/issues) to see if it's already reported.
* If not, open a new issue and provide as much detail as possible:
    * A clear and concise description of the bug.
    * Steps to reproduce the behavior.
    * Expected behavior vs. actual behavior.
    * Your AlluOS version and Host OS (Linux distribution, Python version).
    * Any relevant error messages or screenshots.

### 2. Suggest Enhancements (Feature Requests)

* Have an idea for a new feature or an improvement to an existing one? Open an issue on the [GitHub Issues page](https://github.com/Kiwi8474/AlluOS/issues).
* Clearly describe the proposed feature and its benefits.
* Explain why it would be valuable to AlluOS or its users.

### 3. Improve Documentation

* Good documentation is crucial! If you find typos, unclear explanations, or missing information in the `README.md`, `CHANGELOG.md`, or any other documentation, please submit a pull request.
* You can also contribute by writing new tutorials or "how-to" guides.

### 4. Code Contributions

We welcome code contributions for bug fixes, new features, or new modules/commands.

#### Before You Start Coding:

1.  **Check Issues:** Look through the [existing issues](https://github.com/Kiwi8474/AlluOS/issues) to see if someone is already working on something similar or or if your idea is already being discussed.
2.  **Open an Issue (for new features/major changes):** For new features or significant changes, it's best to **open an issue first** to discuss your idea. This helps ensure it aligns with the project's direction and avoids duplicated effort.
3.  **Fork the Repository:**
    * Go to the [AlluOS GitHub repository](https://github.com/Kiwi8474/AlluOS).
    * Click the "Fork" button in the top right corner.
4.  **Clone Your Fork:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/AlluOS.git](https://github.com/YOUR_USERNAME/AlluOS.git)
    cd AlluOS
    ```
5.  **Create a New Branch:**
    ```bash
    git checkout -b feature/your-feature-name # for features
    # or
    git checkout -b bugfix/description-of-fix # for bug fixes
    ```

#### While Coding:

* **Pythonic Code:** Adhere to Python's [PEP 8 style guide](https://www.python.org/dev/peps/pep-0008/).
* **Testing:** If possible, add tests for new features or bug fixes.
* **Comments:** Add comments where necessary to explain complex logic.
* **Localization:** If you're adding user-facing strings, consider adding them to the language files (`lang_en.json`, `lang_de.json`) and using `get_text()` for internationalization.

#### Adding New Commands or Modules:

AlluOS uses a modular structure, and new functionalities are added either as standalone commands or as larger modules/applications.

* **New Commands (`commands/`):**
    * For simple, standalone commands (like `ls`, `cd`, `nani`), place them directly in the `commands/` directory.
    * **Format Requirement:** Each command file must define an `execute` function with the following signature:
        ```python
        def execute(args, lang_dict, theme_settings, current_user, is_admin):
            # Your command logic here
            return True # Or False on error
        ```
        * `args`: A list of arguments passed to the command.
        * `lang_dict`: The currently loaded language dictionary for localization.
        * `theme_settings`: The current theme settings.
        * `current_user`: The username of the currently logged-in user.
        * `is_admin`: A boolean indicating if the current user has administrator privileges.

* **New Modules/Applications (`modules/`):**
    * For larger, more complex functionalities or applications (like the proposed TDE, DE, or advanced configuration tools), create them as separate modules. These modules will be managed and installed via `apm`.
    * **Packaging:** Modules must be packaged as `.zip` files.
    * **Version Metadata:** Every module **must** include a `_version.json` file at its root level. The filename should start with the module's folder name (e.g., `my_module_version.json` for a module named `my_module`). This JSON file must be formatted as follows:
        ```json
        {
            "name": "Human-readable name of your module",
            "identifier": "unique_module_id",
            "version": "1.0.0",
            "release_date": "DD-MM-YYYY",
            "description": "A short description of what this module does.",
            "author": "Your Name or Organization"
        }
        ```
        * `name`: A user-friendly name for the module.
        * `identifier`: A unique, machine-readable ID for the module (e.g., `tde_module`, `config_helper`). This should typically match the module's folder name when unzipped.
        * `version`: The version number of the module (e.g., semantic versioning).
        * `release_date`: The date the module was released, in `YYYY-MM-DD` format.
        * `description`: A brief summary of the module's purpose.
        * `author`: The creator(s) of the module.

#### Submitting Your Changes (Pull Request):

1.  **Commit Your Changes:**
    ```bash
    git add .
    git commit -m "feat: Add new feature X" # Use meaningful commit messages
    ```
2.  **Push to Your Fork:**
    ```bash
    git push origin your-branch-name
    ```
3.  **Open a Pull Request:**
    * Go to your fork on GitHub.
    * Click the "Compare & pull request" button next to your branch.
    * Provide a clear title and description for your pull request. Explain what your changes do and why they are necessary.
    * Link to any relevant issues (e.g., "Closes #123" or "Fixes #456").

### 5. Translations

* If you'd like to add support for a new language or improve existing translations, please open a pull request with the updated language files in `lang/`.

---

## Contact

If you have any questions, feel free to reach out by opening an issue or discussion on GitHub.

Thank you for making AlluOS better!
