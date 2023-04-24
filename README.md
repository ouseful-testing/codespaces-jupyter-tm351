# TM351 Environment in Github Codespaces Demo

Demo of running an OU maintained Docker container as the computational environment.

The demo is interesting for several reasons:

- a custom container can be provided that defines a complex computational environment for use in the Codespace. In the current example, the container is a container used in the Open University module *TM351 Data Management and Analysis*. This environment includes:
  - a PostgreSQL server with preconfigured user accounts;
  - a MongoDB server seeded with a several data collections;
  - __we can deliver a complex computational environment to students that we can update as required by updating the original Docker image__
  
- Codespaces provide a generous amount of free hosted compute hours per month, meaning an install free user experience;
  - __students can use the Codespaces environment for free withouy any hosting burden on, or costs to, the OU__

- the editing environment is separate from the containerised computational environment. Codespaces can be used to provide install free, customisable, browser based VS Code and JupyterLab environments:
  - the VS Code editor can be customised by installing additional extensions via the `devcontainer.json` file;
  - the JupyterLab editing environment can be customised by installing JuptyerLab extensions via the `requirements.txt` file;
  - __we can separate concerns of delivering a customised computational environmnt (via the Docker image) and a customised user editing environment (via `.devcontainer` config files in the repo)__

- file edits can be persisted in a Github repository using the VS Code and JupyterLab git extensions. (Modified files are persisted in the container and can also be published to a new branch);
  - __provides a natural rationale for getting students into the habit of using version control / git__
  
- *the JupyterLab environment does supports a local file access extension but this doesn't appear to work in this context at the moment...*

- langauge pack extensions can be added to the JupyterLab environmnt; the current environment includes French and Chinese language packs, along with English (the default); change language from the JupyterLab `Settings > Language` menu option;
  - __we can support localised language packs for foreign students, or locally customised labels as required; users can install additional language packs themselves__

*The full TM351 environment includes a proxied OpenRefine server, although this seems to knock the Codespace container over. I think this is because OpenRefine is a resource heavy Java application that seems happiest with at least 4GB of memory available.*

We can specify the default Codespaces editor to be JuptyerLab from the Github user settings page:

<img width="789" alt="image" src="https://user-images.githubusercontent.com/82988/234049241-d4f12077-1c36-4495-977f-f5f95a0dcc57.png">

To access the environment:

- create a Github account;
- click on "Use this template*;
- create a private repository based on the template;
- open a new Codespace from your own repository.

__Note that it may take several minutes for the containr to be built the first time you use it or if you delete the workspace and create a new one. If you stop a workspace and restart it at a later time, the set-up should be quicker.__

When the Codespace container is built, the JupyterLab UI should be automatically opened in your browser with access to that environment.

If you get something like this:

<img width="1255" alt="image" src="https://user-images.githubusercontent.com/82988/234068267-f65fcc61-f18d-49e8-88cd-ba36d4dbdf1f.png">

then hard refresh the browser page.

The intial display may appear a bit broken... Try clicking things to reset the view...

<img width="1061" alt="image" src="https://user-images.githubusercontent.com/82988/234069091-a3c3f024-d92b-4bb8-8077-c484795a0135.png">

A wide variety of JupyterLab extensions are preinstalled in the environment, including a branding pack and cell execution status indicators.

<img width="1254" alt="image" src="https://user-images.githubusercontent.com/82988/234067070-205b4935-52f6-4560-9eb6-e5b161033056.png">

[Empinken styling](https://github.com/innovationOUtside/jupyterlab_empinken_extension) is supported, and a growing number of MyST styling features are supported by the [`jupyerlab-myst` extension](https://github.com/executablebooks/jupyterlab-myst).

<img width="664" alt="image" src="https://user-images.githubusercontent.com/82988/234069968-407e3392-df98-450a-a1c4-b36f12f77e75.png">

The pre-installed `jupyterlab-git` extension allows you to commit and push changes back to the code repository.

<img width="1260" alt="image" src="https://user-images.githubusercontent.com/82988/234066314-4c1089ab-a592-403f-b72a-792d3e454ca5.png">
