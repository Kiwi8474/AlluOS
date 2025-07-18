# AlluOS: Your Portable Python CLI System for Development and Learning

---

## About AlluOS

AlluOS is a **lightweight, Python-based command-line operating system** specifically designed as a **learning project and a sandbox for developers**. It's not intended to replace your daily OS, but rather to provide a controlled and modular environment for understanding how a CLI system works, developing custom commands, and experimenting with file system interactions.

**Please note: AlluOS currently runs only on Linux systems.**

### What AlluOS Can Do:

* **Modular Core:** AlluOS is built with modularity at its heart. New functionalities and commands can be easily added as Python modules, similar to packages in a real OS. This allows you and other developers to extend the system as you wish.
* **Your Own Shell Interpreter (`sh`):** You can write your own scripts composed of AlluOS-internal commands, executed line by line. This acts as a simple scripting language unique to AlluOS, enabling modules to communicate with each other.
* **External Python Script Execution (`pyexec`):** Beyond internal scripts, you can also run external Python files directly from AlluOS by downloading and installing the pyexec module from the mirror server. This leverages your host system's Python interpreter, granting you the full power of Python and its libraries.
* **Secure Sandbox:** All operations are confined to the AlluOS root directory, providing a safe environment for experimentation without affecting your host system.
* **Customizable:** AlluOS supports theming and currently offers **English and German language translations**, allowing you to personalize your environment.

---

## Pre-installed Programs & Commands

Each pre-installed program in AlluOS is a modular command you can extend or modify.

* **`help`:** Lists all available commands.
* **`clear`:** Clears the AlluOS terminal.
* **`ls` (List Files):** Displays the contents of the current directory.
    * `ls`
* **`cd` (Change Directory):** Changes the current working directory.
    * `cd <directory_name>`
    * `cd ..` (Navigates to the parent directory)
* **`mkdir` (Make Directory):** Creates a new directory.
    * `mkdir <directory_name>`
* **`mv` (Move):** Moves or renames files and directories.
    * `mv <source> <destination>`
* **`cp` (Copy):** Copies files and directories.
    * `cp <source> <destination>`
* **`rm` (Remove):** Deletes files and directories. **Caution!** Irreversible after confirmation.
    * `rm <filename>`
    * `rm -r <directory_name>` (Recursively deletes directories)
* **`nani` (Text Editor):** A simple text editor for creating and modifying files directly within the AlluOS shell.
    * `nani <filename>` (Opens or creates the file)
    * **Nani Commands (within the editor, type after the `:` prompt):**
        * `w`: Save the current file.
        * `q`: Quit the editor (prompts to save if unsaved changes exist).
        * `q!`: Force quit (discards changes without saving).
        * `wq`: Save and quit.
        * `e <line_number>`: Edit a specific line. Example: `e 5` to edit line 5.
        * `i <line_number>`: Insert new lines before a specific line. Type `!!end!!` on a new line to finish insertion.
        * `a <line_number>`: Insert new lines after a specific line. Type `!!end!!` on a new line to finish insertion.
        * `d <line_number>`: Delete a specific line. Example: `d 10` to delete line 10.
        * `next`: Scroll down 20 lines to view more content.
        * `prev`: Scroll up 20 lines to view previous content.
* **`sh` (Shell Script Executor):** Executes scripts composed of internal AlluOS commands. Perfect for automation within the AlluOS environment.
    * `sh <scriptfile.alluos>` (or any file extension)
* **`sudo` (SuperUser Do):** Allows commands to be executed with elevated administrator privileges within AlluOS (if not available to the current user).
    * `sudo <command>`
* **`apm` (AlluPackageManager):** The package management system for AlluOS, allowing you to install, update, or remove additional modules and commands.
    * `apm install <package_name>`
    * `apm update`
    * `apm list`
    * `apm uninstall <package_name>`
    * `apm <package_name> version`
* **`version`:** Displays the current version of AlluOS and its core components.
* **`exit`:** Exits AlluOS.

---

## Installation & Getting Started

1.  **Prerequisites:** You only need **Python 3.12.3** installed on your Linux system.
2.  **Download:** Download the latest stable version of AlluOS (or any version you desire):
    * **[Download AlluOS 1.1.1 (GitHub Release)](https://github.com/Kiwi8474/AlluOS/releases/tag/1.1.1)**
    * **[Download AlluOS 1.1.1 (Mirror Server)](http://apm-mirror.duckdns.org/alluos_releases/AlluOS_1.1.1_06-07-2025_stable.zip	)**
    * *Note: The mirror server offers potentially faster or alternative downloads if GitHub is unreachable. Even though it says, that the files from the mirror server are potentially unsafe, it is 100% guaranteed to be safe.*
3.  **Extract:** Extract the downloaded `AlluOS_1.1.1_06-07-2025_stable.zip` file to a directory of your choice.
4.  **Get a bootloader:** The `_stable.zip` releases provide a bootloader to use. You can also program your own bootloader, but the provided one is recommended.
5.  **Launch:** Open a terminal, navigate into the directory where AlluOS lies, and run the following command:
    ```bash
    python3 alluboot.py
    ```

---

## Contributing & Contact

AlluOS is an open-source project. We welcome contributions, bug reports, and feature suggestions!

* **Issues:** Report bugs or suggest new features on the [GitHub Issues page](https://github.com/Kiwi8474/AlluOS/issues).
* **Contributions:** Check out our [Contributing Guidelines](CONTRIBUTING.md) if you'd like to contribute code.

---

## File & Folder Paths of Newest Version

This is the pathtree of the newest AlluOS version without any modules installed:

```
AlluOS/
   config/
      installed_modules.json
      lang_de.json
      lang_en.json
      settings.json
      users.json
      versions.json
   home/
   modules/
   system/
      commands/
         __init__.py
         apm.py
         cd.py
         clear.py
         cp.py
         echo.py
         exit.py
         help.py
         ls.py
         mkdir.py
         mv.py
         nani.py
         rm.py
         sh.py
         version.py
      __init__.py
      auth_manager.py
      command_dispatcher.py
      config_manager.py
      core.py
      display_utils.py
      main.py
      path_manager.py
      setup_routines.py
   tmp/
```

### But what are the folders even used for?

* **config/:** This is the folder where all the json config files lie.
* **home/:** This is the home directory for the users.
* **modules/:** This folder is empty - even after the setup. It is used for installed modules that aren't command-based (like a "Desktop Environment").
* **system/:** Here are the most important files. It's the heart of AlluOS.
* **tmp/:** This folder is normally empty. It is used by AlluPackageManager as a temporary folder for the downloaded zip packages, which are deleted after installing.

---

## Structure of an APM package

This is the structure an APM package should have. Otherwise it won't work with APM.

```
<package_name>.zip/
   <command_name>.py
   <package_name>_version.json
```

### Explanations of the files
* **<package_name>.zip/:** This is the package itself. It should only contain the two files mentioned above.
* **<command_name>.py:** This is the command file. The name of the file will be the command name that you can enter to run the module.
* **<package_name>_version.json:** This is the json file that contains all of the metadata.

### Content of the files

* **<command_name>.py:**
```
# This is the base template of a command
# You can also put imports of the system/ files here (e.g. "from display_utils import apply_theme" for color themed text)
def execute(args, lang_dict, theme_settings, current_user, is_admin):
   return True # Not really needed but good to use
```
* **<package_name>_version.json:**
```
{
    "name": "", // Human readable name of your package
    "identifier": "", // unique identifier ID
    "version": "", // newest version of your package
    "release_date": "", // release date of your newest package
    "description": "", // quick description. 1-2 sentences
    "author": "" // your name
}
```

---
