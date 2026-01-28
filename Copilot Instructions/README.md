# Writing your own copilot-instructions.md file

- In the root of your repository, create a file named .github/copilot-instructions.md.
- Create the .github directory if it does not already exist.
- Add natural language instructions to the file, in Markdown format.
- Whitespace between instructions is ignored, so the instructions can be written as a single paragraph, each on a new line, or separated by blank lines for legibility.

# Creating path-specific custom instructions

- Create the .github/instructions directory if it does not already exist.
- Create one or more NAME.instructions.md files, where NAME indicates the purpose of the instructions. The file name must end with .instructions.md.
- At the start of the file, create a frontmatter block containing the applyTo keyword. Use glob syntax to specify what files or directories the instructions apply to.

For example:
---
applyTo: "app/models/**/*.rb"
---
You can specify multiple patterns by separating them with commas. For example, to apply the instructions to all TypeScript files in the repository, you could use the following frontmatter block:
---
applyTo: "**/*.ts,**/*.tsx"
---
Glob examples:
* - will all match all files in the current directory.
** or **/* - will all match all files in all directories.
*.py - will match all .py files in the current directory.
**/*.py - will recursively match all .py files in all directories.
src/*.py - will match all .py files in the src directory. For example, src/foo.py and src/bar.py but not src/foo/bar.py.
src/**/*.py - will recursively match all .py files in the src directory. For example, src/foo.py, src/foo/bar.py, and src/foo/bar/baz.py.
**/subdir/**/*.py - will recursively match all .py files in any subdir directory at any depth. For example, subdir/foo.py, subdir/nested/bar.py, parent/subdir/baz.py, and deep/parent/subdir/nested/qux.py, but not foo.py at a path that does not contain a subdir directory.
Optionally, to prevent the file from being used by either Copilot coding agent or Copilot code review, add the excludeAgent keyword to the frontmatter block. Use either "code-review" or "coding-agent".

For example, the following file will only be read by Copilot coding agent.

---
applyTo: "**"
excludeAgent: "code-review"
---
If the excludeAgent keyword is not included in the front matterblock, both Copilot code review and Copilot coding agent will use your instructions.
Add your custom instructions in natural language, using Markdown format. Whitespace between instructions is ignored, so the instructions can be written as a single paragraph, each on a new line, or separated by blank lines for legibility.


interesting projects:
https://github.com/github/awesome-copilot

