# Quiz CLI

An interactive command-line quiz game for learning JavaScript and programming fundamentals.

> A small, dependency-free Node.js CLI that runs quizzes from a JSON question bank. Ideal for learning and demoing Node.js features and CLI patterns.


## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [File Structure](#file-structure)
- [Configuration](#configuration)
- [Scripts / Commands](#scripts--commands)
- [Contributing](#contributing)
- [License](#license)


## Project Overview

Quiz CLI is a small, dependency-free Node.js command-line application that runs interactive quizzes from a JSON question bank. It is designed as an educational demo showcasing common Node.js and JavaScript patterns: ES modules, async/await, file system access, user input handling, classes, and array utilities.

The runnable application is located in the `test-app` folder and is suitable for learners, instructors, or anyone who wants a lightweight CLI quiz tool.

## Features

- Interactive terminal-based quiz with multiple categories (JavaScript, Node.js, General Programming)
- Questions and answers are loaded from a JSON file (test-app/data/questions.json)
- Choose how many questions to attempt (All / 3 / 5) when available
- Shuffled questions each run (Fisher–Yates shuffle)
- Progress bar and per-question feedback (correct/incorrect)
- Explanations for questions when provided
- Review incorrect answers at the end of the quiz
- Colored output using ANSI escape codes (no external dependencies)
- Minimal, modular source organized under test-app/src

## Prerequisites

- Node.js v18.0.0 or newer (project uses ES Modules and node: built-ins)
- npm (optional, for running scripts)

## Installation

1. Clone this repository:

   git clone <repo-url>

2. Change into the app directory:

   cd test-app

3. (Optional) Install dependencies. This project has no runtime dependencies, but you can still run:

   npm install

## Usage

From the `test-app` directory run:

- Start the app with npm:

  npm start

- Or run directly with node:

  node index.js

How it works:
- Choose a category from the list.
- Choose how many questions you want to attempt (if the category supports it).
- Answer each question by entering the option number.
- Press Enter to continue between questions.
- At the end you'll see your score, performance message, and a review of incorrect answers.

Example session (commands shown):

  cd test-app
  npm start

Then follow interactive prompts in the terminal.

## Customizing Questions

Questions are stored in `test-app/data/questions.json` and follow this structure:

{
  "categories": {
    "categoryId": {
      "name": "Category Name",
      "questions": [
        {
          "question": "Question text",
          "options": ["opt1", "opt2", "opt3"],
          "answer": 0, // index of correct option (0-based)
          "explanation": "Optional explanation text"
        }
      ]
    }
  }
}

Add or modify categories and questions and re-run the app.

## File Structure

- /test-app
  - index.js            — App entry point, CLI flow and orchestration
  - package.json        — Project metadata and npm scripts (start/test)
  - /src
    - input.js          — Readline helpers and user prompt utilities
    - quiz.js           — Quiz class and game logic (shuffling, scoring)
    - colors.js         — Small ANSI color helpers for terminal output
  - /data
    - questions.json    — Question bank organized by categories

Other files at repo root (for repository management):
- .gitignore

## Implementation Notes

- Uses ES module syntax (import/export) and Node built-in modules like `fs/promises`, `path`, and `url`.
- Questions are loaded with `fs.promises.readFile` and parsed as JSON.
- The Quiz class shuffles questions and tracks score, answers, and progress; incorrect answers are summarized at the end.

## Scripts / Commands

- npm start  — Runs `node index.js` (from test-app)
- npm test   — Runs `node --test` (no test files included by default; placeholder)

Run scripts from the `test-app` directory, or prefix with `--prefix` from repo root:

  npm --prefix test-app start

## Configuration

- No environment variables are required to run the app.
- Node.js version is specified in `test-app/package.json` under `engines` (>=18.0.0).

## Testing

There are no formal tests included in this repository. The `test` script in package.json runs `node --test` and can be used as a placeholder if you add Node.js tests later.

## Contributing

Contributions are welcome. Suggestions:

- Add more categories and questions to `test-app/data/questions.json`.
- Add unit tests for the Quiz logic and input helpers.
- Improve UX (keyboard navigation, timed quizzes, scoring breakdowns).

When contributing, please open a pull request and describe the change.

## License

This project is licensed under the MIT License. See the `test-app/package.json` for the declared license.


<!-- End of README -->
