# 🛠 Contribution Guide

Before you start contributing to **Daily Slack Notification**, please read through the guidelines below to ensure a smooth and organized contribution process.

## 1️⃣ How to Contribute

### 🧑‍💻 Fork the Repository

1. **Fork** the repository to your GitHub account by clicking the *Fork* button in the top right of the repository page.
2. Clone the forked repository to your local machine:

    ```sh
    git clone https://github.com/your-username/daily-slack-notification.git
    cd daily-slack-notification
    ```

### 🔄 Create a New Branch

Always create a new branch for each new feature or bug fix. Use a descriptive name for the branch. For example, if you're fixing a formatting bug, use:

```sh
git checkout -b fix/bug-formatting
```

### ✍️ Make Your Changes

Make the changes or fixes you want to contribute to the code.

### 🚀 Test Your Changes

- If it's a bug fix, make sure the tests are passing.
- If it's a new feature, create new tests if necessary.

To run the tests, use the command:

```sh
python -m unittest discover -s tests
```

### 📝 Update Documentation

If needed, update the project's documentation (README or related files) to reflect the changes, such as new dependencies or configurations.

### 📤 Commit Your Changes

Commit your changes with a clear and concise message. Follow this commit message format:

```
<type>(<scope>): <message>
```

Example:

```
feat(api): add daily notification scheduling functionality
```

Common commit types are:

- **feat**: new feature
- **fix**: bug fix
- **docs**: documentation changes
- **style**: code formatting (no logic changes)
- **refactor**: code refactoring
- **test**: adding or modifying tests

### 📤 Push Your Changes

Push your branch to your remote repository:

```sh
git push origin your-branch-name
```

2. Go to your repository on GitHub and click *Compare & pull request*.
3. Provide a brief description of what has changed and why.
4. Submit the pull request for review.

## 2️⃣ Review and Feedback

- After you submit a pull request, the project team will review the changes.
- If necessary, adjustments may be requested before merging your contribution.
- Be responsive to feedback and make the necessary changes as requested.

## 3️⃣ Code Standards

This project follows some code standards to ensure that the codebase is organized and maintainable:

- **Indentation**: Use 4 spaces for indentation. Do not use tabs.
- **Variable names**: Use camelCase for variables and functions.
- **Spaces**: Add a blank line between functions and classes.
- **Imports**: Organize imports according to Python conventions.

## 4️⃣ How to Test Locally

### Prerequisites

- **Python 3.9+** installed.
- Dependencies installed with:

    ```sh
    pip install -r requirements.txt
    ```

### Running Tests

To run the tests automatically, use the command:

```sh
python -m unittest discover -s tests
```

Or, if you prefer to run the script manually:

```sh
python scripts/daily_slack.py
```

## 5️⃣ Opening Issues

If you encounter any bugs or have suggestions for improvements, feel free to open an **issue** in the repository. Please provide as many details as possible, including:

- Steps to reproduce the issue.
- Expected behavior.
- Screenshots or logs, if applicable.

---

## 🙏 Thank You for Contributing!

Thank you for considering contributing to **Daily Slack Notification**! Your contribution helps improve the project and makes it more useful to everyone.
