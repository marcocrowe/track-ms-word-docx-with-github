
# [Track changes in MS Word documents using GitHub and Pandoc](https://github.com/marcocrowe/track-ms-word-docx-with-github/)

Track changes in MS Word (.docx) files using GitHub and Pandoc for effective version control and collaboration.

## 1. Install Required Software

- **Pandoc**: Install Pandoc on your system. It’s a tool that converts `.docx` files to Markdown format, which Git can track more effectively. Download Pandoc from [Pandoc's official site](https://pandoc.org/installing.html) and follow the installation instructions for your operating system. Generally the version for Windows ends with `-windows-x86_64.msi` and is an `.msi` installer, while for macOS it’s a `.pkg` installer.
- **GitHub Desktop**: Ensure that GitHub Desktop is installed and set up on your computer. If you don’t have it yet, you can download it from [GitHub Desktop’s official site](https://desktop.github.com/).

## 2. **Update Your `.gitconfig` File**

The `.gitconfig` file is a configuration file for Git that can be used to set up custom configurations. In this case, we will use it to tell Git to use Pandoc to convert `.docx` files to Markdown format for better tracking.

Your `.gitconfig` file can be located in your user’s home directory or the root (e.g. [c:/users/user/.gitconfig](c:/users/user/.gitconfig)) of your repository. You can modify it to add the following:

Open your `.gitconfig` file and add the following lines:

```git
# Using Microsoft Word with git
# https://github.com/marcocrowe/track-ms-word-docx-with-github
[diff "pandoc"]
    textconv=pandoc --to=markdown
    prompt = false
[alias]
    wdiff = diff --word-diff=color --unified=1
```

Save the file. This tells Git to use Pandoc to convert `.docx` files to Markdown when performing diffs, which allows you to see what has changed inside Word documents in a readable format.

## 3. Enable a Repository for Word Document Tracking

For any repository where you want to track changes in `.docx` files, you need to set up the repository to use Pandoc for conversion. This involves creating or updating a `.gitattributes` file in the repository.

- **Create or Update `.gitattributes` File**:
  - Open your Git repository folder.
  - Create a new file `.gitattributes` in the root directory of your repository or if it already exists, open it.
  - Add the following lines to the `.gitattributes` file.

```git
# Use Pandoc to track changes in .docx files
# https://github.com/marcocrowe/track-ms-word-docx-with-github
*.docx diff=pandoc
```

Save the file. This configuration ensures that Git (and by extension, GitHub Desktop) will use Pandoc to convert `.docx` files to a text format before showing differences.

### Open the Repository in GitHub Desktop

Open the repository in GitHub Desktop. You should now be able to see changes in `.docx` files in a more readable format.

---

Copyright &copy; 2024 Mark Crowe <https://github.com/marcocrowe>. All rights reserved.
