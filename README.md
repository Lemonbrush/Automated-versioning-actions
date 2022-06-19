# Automated version increment

This repo has version increment automatization based on version txt file and script

### How this works:

- add VERSION.txt file to the project and type some initial version into it. Like 0.0.0
- branch from development with branch prefixes "release", "feature", "bugfix", "alpha", "beta", "rc"
 - example: feature/add-some-feature
- add changes
- merge your branch into development via pull request
- the github actions workflow will automatically parse the merge commit, find prefix, increment semantic version in the version file and commit changes into development branch

### Additional:

There is a .githook folder with pre-commit hook. You can apply branch prefix check by adding the hook with the following command:

git config core.hooksPath .githooks

This pre-commit hook will prevent commiting into branch without needed prefixes
