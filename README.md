# Github-Action-Tutorial

## Introduction to this repository

### What? 

The goal with this repository is to help and illustrate how to do the following things: 
- Learn about Github Actions
- Use Github Actions 
- Build Github Actions

If you would like to use github actions or want inspiration I recomend (this)[https://github.com/sdras/awesome-actions] repository. 


### Why?

I found it hard to learn about how to set up and use github actions and there are some tricks that are not well documented. In order to help others and document my own findings I create this repository. 


### How? 

Examples that can be used will be created and illustrated. 


## What is a Github Action vs Workflow? 

A Github Workflow defines what to do when. When could be: 

- An event on GitHub occurs, such as when someone pushes a commit to a repository or when an issue or pull request is created.
- A scheduled event begins.
- An external event occurs.

The workflow needs to be saved in ```root_of_repository/.github/workflows/your_workflow.yml ``` and needs to have ".yml" I would also recomend to set the name to something that illustrate the workflow, since this will be the name set in the Actions tab on Github. 

Exemple workflow: 

```yaml
name: Pull request check
on:
  pull_request:
    types: [opened]

```

- An external event occurs.
More info can be found [here](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow#triggering-a-workflow-with-events). 

The what to do is defined as [jobs](https://help.github.com/en/actions/getting-started-with-github-actions/core-concepts-for-github-actions#job), each workflow needs to have at least one job. 

Exemple workflow: 

```yaml
name: Pull request check
on:
  pull_request:
    types: [opened]

jobs:
  first-job:
```

Each job can have one or multiple steps. A step is described by [github](https://help.github.com/en/actions/getting-started-with-github-actions/core-concepts-for-github-actions#job) like this: 

"""
A step is a set of tasks performed by a job. Each step in a job executes in the same runner, allowing the actions in that job to share information using the filesystem. Steps can run commands or actions.
"""

```yaml
name: Pull request check
on:
  pull_request:
    types: [opened]

jobs:
  first-job:
    runs-on: [ubuntu-latest]
    steps:
```
[Runner](https://help.github.com/en/actions/getting-started-with-github-actions/core-concepts-for-github-actions#runner) is the type of machine the action is executed on there are a couple of options supplied by github. 

- Windows Server 2019:	windows-latest or windows-2019
- Ubuntu 18.04:	ubuntu-latest or ubuntu-18.04
- Ubuntu 16.04:	ubuntu-16.04
- macOS Catalina 10.15:	macos-latest or macos-10.15

A step can execute pretty much what ever you like on "your" assigned machine. However the best-practice way to do more complex processes are to use Github Actions. Actions will be describe in the next session.
```yaml
name: Pull request check
on:
  pull_request:
    types: [opened]

jobs:
  first-job:
    runs-on: [ubuntu-latest]
    steps:
     - name: What ever you like
        run: |
            echo "Hello world" 
```


## How do you use Github Actions? 


``` txt
You can create actions by writing custom code that interacts with your repository in any way you'd like, including integrating with GitHub's APIs and any publicly available third-party API. For example, an action can publish npm modules, send SMS alerts when urgent issues are created, or deploy production-ready code.

```

## How do you build your own Github Actions? 

