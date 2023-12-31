# Repbox via Github Actions

-- WORK IN PROGRESS --

This repositorium can be adapted to run a repbox analysis via Github actions. 







## 1. Usage

0. Get a Github account. 

1. If you already know Git: Fork this repository so that you have admin rights and can modify it. Create a local version that you can modify.

Alternatively, download the ZIP file and extract it to your folder.

2. Provide the supplement and article for which you want to perform the repbox analysis. There are different ways:

**Local** Create a local version of the forked repository. Generally, helpful is software like [Github Desktop](https://desktop.github.com/). Then copy a ZIP of the supplement into the `sup` directory and the article files as PDF, HTML or ZIP into the `art` directory. Afterward comit your 

**Download**  

3. Set the required secrets for your repository. (See next section for details)

4. (Optional) Adapt settings for repbox run.

5. Make sure you have commited all changes and then trigger the run. 

## 2. Required secrets

To set secrets using a shell script, you can use the [Github cli](https://cli.github.com/) command line utility. Alternatively, you either set the secrets manually on the repositories Githhub page ([see here](https://github.com/Azure/actions-workflow-samples/blob/master/assets/create-secrets-for-GitHub-workflows.md)). 

For both approaches set all secrets as *plain text*, no base64 encoding.

You require the following secrets:

- STATA_LIC: Plain text of your Stata license. You need a valid Stata license to use the framework.

- REPBOX_ENCRYPT_KEY Key to extract the not yet public R packages.  
