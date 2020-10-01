
This is a workflow repository powered by [Actionsflow](https://github.com/actionsflow/actionsflow), generated from [actionsflow/actionsflow-workflow-default](https://github.com/actionsflow/actionsflow-workflow-default)

# 🏁 Getting Started <a name = "getting_started"></a>

Build an Actionsflow workflow is a three-step process:

1. **Create a public Github repository by this [link](https://github.com/actionsflow/actionsflow-workflow-default/generate).**

   A typical Actionsflow repository structure looks like this:

   ```sh
   ├── .github
   │   └── workflows
   │       └── actionsflow.yml
   ├── .gitignore
   ├── README.md
   └── workflows
   │   └── rss.yml
   │   └── webhook.yml
   └── package.json
   ```

1. **Define your [workflow file](https://actionsflow.github.io/docs/workflow/) at `workflows` directory**

   A typical workflow file `rss.yml` looks like this:

   ```yaml
   on:
     rss:
       url: https://hnrss.org/newest?points=300
   jobs:
     ifttt:
       name: Make a Request to IFTTT
       runs-on: ubuntu-latest
       steps:
         - uses: actionsflow/ifttt-webhook-action@v1
           with:
             event: notice
             key: ${{ secrets.IFTTT_KEY }}
             value1: ${{on.rss.outputs.title}}
             value2: ${{on.rss.outputs.contentSnippet}}
             value3: ${{on.rss.outputs.link}}
   ```

   For more information about the Actionsflow workflow file, see the
   [Actionsflow workflow reference](https://actionsflow.github.io/docs/workflow/).

   You can explore [Triggers List](https://actionsflow.github.io/docs/triggers/) or [Awesome Actionsflow Workflows](https://github.com/actionsflow/awesome-actionsflow) to get more inspired.

1. **Commit and push your updates to Github**

Then, Actionsflow will run your workflows as you defined, you can view logs at your repository actions tab at [Github](https://github.com)

For more information, see [Full documentation](https://actionsflow.github.io/docs/)

## Run manually

The power of Actionsflow comes from the Github workflow file [`.github/workflows/actionsflow.yml`](./.github/workflows/actionsflow.yml), usually, Actionsflow runs with [`a per 5 minutes' scheduled event`](https://docs.github.com/en/free-pro-team@latest/actions/reference/events-that-trigger-workflows#scheduled-events), but you can also run it manually by [`workflow_dispatch` event](https://docs.github.com/en/free-pro-team@latest/actions/managing-workflow-runs/manually-running-a-workflow). Click Actions tab of your repository, and click `Run workflow` at `Actionsflow` workflow.

For more information, see [Manually running a workflow](https://docs.github.com/en/free-pro-team@latest/actions/reference/events-that-trigger-workflows#scheduled-events)


## Run Locally

You can run Actionsflow locally for testing your workflow files.

### Install

```bash
npm install
```

### Build

```bash
npm run build
# Then, the standard workflow files will be built at ./dist/workflows
```

### Clean

Actionsflow build will use cache for deduplicating the data, if you want to test your workflow with the same data, you may need to clean the cache by the following command:

```bash
# Clean the cache and dist folder.
npm run clean
```

> If you want to run workflows built by Actionsflow locally, you should use `npm run act`, for more information, see [act](https://github.com/nektos/act)

# 🎓 Learn More <a name="reference"></a>

Full documentation for Actionsflow lives [on the website](https://actionsflow.github.io/docs/).

- [Workflow Syntax for Actionsflow](https://actionsflow.github.io/docs/workflow/) - Learn more about the Actionsflow workflow file syntax
- [Triggers List](https://actionsflow.github.io/docs/triggers/) - Explore Actionsflow triggers
- [Awesome Actionsflow Workflows](https://github.com/actionsflow/awesome-actionsflow) - Explore Actionsflow workflows use case to get inspired
- [Core Concepts](https://actionsflow.github.io/docs/concepts/) - Learn more about how Actionsflow worked
- [Creating Triggers for Actionsflow](https://actionsflow.github.io/docs/creating-triggers/) - Learn more about how to create your own trigger for Actionsflow
- [FAQs](https://actionsflow.github.io/docs/faqs/) - Actionsflow FAQs
- [Upgrade Guide](https://actionsflow.github.io/docs/upgrade/)
