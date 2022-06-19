# Automated version increment

This repo has version increment automatization

How this works:

- add VERSION.txt file to the project and type some initial version into it. Like 0.0.0
- branch from development
- add changes
- merge your branch into development via pull request
- the github actions workflow will automatically increment version in the version file and a commit into development

