bika.devtools
=============

commands to manage branch-per-feature development

- http://www.acquia.com/blog/pragmatic-guide-branch-feature-git-branching-strategy

These scripts assume a certain workflow:

- bpf.json specifies a list of integration branches, and the features they will each contain.  
- All "git bpf" commands automatically sync the "bika.devtools" repository.
- if git rerere is enabled (it should be), the .git/rr-cache folder must be linked to bika.devtools/rr-cache/xxx.

### git bpf pull xxx-integration

Pull all feature branches specified in xxx-integration, including the base
branch.

### git bpf push xxx-integration

Push all commits in all branches that are specified as features of
xxx-integration branch, including the base branch.

### git bpf sync xxx-integration

push and pull.

### git bpf rebuild xxx-integration

    - checkout xxx
    - create/reset new branch xxx-integration
    - <for each feature branch: merge feature branch>

### git bpf update `feature-branch`

All work takes place directly in the xxx-integration branch, and commits
are also made, directly on the xxx-integration branch.

    - <git bpf rebuild xxx-integration>
    - ... Do some work <commit>
    - ... Do some more work <another commit>

To move/save these commits into a feature branch, run this:

   - git bpf update `feature-branch-name`

This will move the new commits into `feature-branch` and then rebuild
the xxx-integration branch.

