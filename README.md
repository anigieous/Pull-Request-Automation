# Pull Request Automation

This repository contains a set of GitHub Actions that automate various aspects of Pull Requests (PRs). It aims to streamline the PR process, making it more efficient and consistent.

## Introduction 
Reusable workflows in github actions for PR Automation

## Available templates <a name="current-templates"></a>

| Name                 | Description |
| -----------          | ----------- |
| Create PR            | GitHub action which helps in creation of Pull Request |
| Update PR              | GitHub action which helps in Updating of Pull Request |
| Merge PR            | GitHub action which helps in Merging the Pull Request |
| Create Label           | GitHub action which helps in Creating Label  |
| Attach Label           | GitHub action which helps in Attaching Label in Pull Request |

## Usage for Create PR 
> Use PAT Token!!
```
jobs:
  Create_PR:
    runs-on: your_runner
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Create Pull Request
        uses: anigieous/Pull-Request-Automation/Create@main
        with:
          token: ${{ secrets.your_github_token }}
          title: 'PR_TITLE'
          body: 'PR_BODY'
          head: ${{ github.ref }}
          base: 'TARGET_BRANCH'
          owner: 'OWNER_NAME'
          repo: 'REPO_NAME'
          label: 'LAEBL'
```


## Usage for Merge PR
> Use PAT Token!!
```
jobs:
  MERGE_PR:
    runs-on: your_runner
    steps:
      - name: Auto Merge PRs
        uses: anigieous/Pull-Request-Automation/Merge@main
        with:
          owner: ${{ github.event.pull_request.user.login }}
          repoName: ${{ github.event.repository.name }}
          prID: ${{ github.event.pull_request.number }}
          prTitle: ${{ github.event.pull_request.title }}
          prBody: ${{ github.event.pull_request.body }}
          GITHUB_TOKEN: ${{ secrets.YOUR_PAT_TOKEN }}
```

## Usage for Update PR
```
jobs:
  UPDATE_PR:
    runs-on:your_runner
    steps:
      - name: Create Pull Request
        uses: anigieous/Pull-Request-Automation/Update@main
        with:
          token: ${{ secrets.YOUR_PAT_TOKEN }}
          title: 'UPDATED_TITLE'
          body: 'UPDATED_PR_BODY'
          owner: 'OWNER'
          repo: 'REPO_NAME'
          pull_number: 'PR_NUMBER'
```
## Usage for Create Label
```
- name: Create Label
  uses: anigieous/Pull-Request-Automation/Label/Create@main
  with:
    label : LABEL
    token: ${{ YOUR_PAT_TOKEN }}
```
## Usage for Attach Label
```
- name: Add Fail label
  uses: anigieous/Pull-Request-Automation/Label/Attach@main
  with:
    token: ${{ YOUR_PAT_TOKEN }}
    label: LABEL
    prID: PR_NUMBER
```   

