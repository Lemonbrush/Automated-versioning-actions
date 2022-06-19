# Automated version increment

This repo has [semantic version](https://semver.org) increment automatization based on version txt file and script

The script is placed in the **.project_scripts** hidden folder  
You can run it manually. To do so you need to create a VERSION.txt file in the root directory and run the script with allowed prefix as an argument  

Allowed prefixes:  
**release** | **feature** | **bugfix** | **alpha** | **beta** | **rc**

Terminal command example:  
**.project_scripts/Version_Increment.sh release**

## How this works:  

The **Development_semver_increment.yml** workflow extracts the semantic version fragment from the last commit with the following regular expression  

regexp: \[release]|\[feature]|\[bugfix]|\[alpha]|\[beta]|\[rc]|release/|feature/|bugfix/|alpha/|beta/|rc/    

Then runs the version increment script which updates the version file with incremented version and commit the changes

### Example steps: 

- add VERSION.txt file to the project and type some initial version into it. Like 0.0.0
- branch from development with one of the branch prefixes "release", "feature", "bugfix", "alpha", "beta", "rc"
  - **example:** feature/add-some-feature
- add changes
- merge your branch into development via pull request
- the github actions workflow will automatically parse the merge commit, find prefix, increment semantic version in the version file and commit changes into development branch

*you also can trigger the workflow by commit name with the prefix in brackets like this "[feature] commit message"  

## Additional:

There is a .githook folder with a pre-commit hook. You can apply branch prefix check by adding the hook with the following command:

**git config core.hooksPath .githooks**

This pre-commit hook will prevent commiting into a branch with wrong prefix
