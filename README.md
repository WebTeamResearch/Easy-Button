# Easy-Button v1.2.4
The app we all want

# Description
Example repo on how to manage branches and merging. This strategy is a way that allows for multiple features on a repository to work well with maximum flexibility and minimal blocking due to not ready to release or don't merge yet scenarios.

### Branches ("" used on branch to represent that it has a custom name):
- master (code in production)
- development (code staged for next release)
- "feature" E.g. f1234-make-button (future capability)
- "epic" E.g. e-lots-o-features (group of features that cannot be released yet)
- "release" E.g. r-v1.2.3 (staged release; update version numbers; etc.)

### Events with Branching [from-branch (merge type) => to-branch]
Feature starts: 
- development => (new) "feature"
- work committed to "feature"

Feature completes: 
- create pull request from feature branch to development branch
- complete peer review (in GitHub), testing, and rework until accepted by reviewer
- "feature" (squash merge) => development
- delete "feature" branch

Ready for release: 
- development => (new) "release"
- updates are made based on user feedback, version updates, etc.
- deploy solution to production
- "release" (merge commit) => master
- create tag on master branch with version, assignment number, and major features/notes
- delete "release" branch
- master (merge commit) => development (update development with any release changes)

### Epic Exceptions 
Epic starts:
- development => (new) "epic"

Epic feature starts:
- "epic" => (new) "feature"
- work committed to "feature"

Epic feature completes:
- "feature" (squash merge) => "epic"
- delete "feature" branch

Epic ready for production:
- "epic" (merge commit) => development
- delete "epic" branch
- Continue with "Ready for release"

*Note 1*: there can as many feature and epic branches as needed, but remember the longer the code stays branched the harder it will be to integrate so keep these branches as small as reasonably possible.

*Note 2*: master and development branches are the only ones that are *NEVER* deleted. development branches from master initially.
