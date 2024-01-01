# Repbox (pilot version) via Github Actions

This repository can be adapted by data editors to run a repbox analysis via Github actions.

A short usage guide is below, but more details are in this screencast:

https://youtu.be/T7DWBMzKboQ

The repbox project is far from being polished, but hopefully (ideally with some DFG funding) it will be converted into a robust, useful tool. If you test it as a data editor and encounter problems or have feature suggestions, you can send me an email or file issues on Github here:

https://github.com/repboxr/repboxIssues/issues

Please don't use the pilot version of repbox yet for any meta studies. (For meta studies there is some more way to go and I first want to test and fix everything by conducting some meta studies myself.)


## Short Usage Overview (First Time Usage)

This list is just a reminder of the steps, you need to do. For an explanation see my [video tutorial](https://youtu.be/T7DWBMzKboQ).

1. Get a Github account. (It's free).

2. Create a local version of this repo that you can modify (fork, clone, or just download the ZIP).

3. Copy your article into the `/art` directory and a ZIP file of your supplement into the `/sup` directory. If you use a public repository and want to encrypt the input and output see point 8.

4. Upload your changes to Github. Unless you already use Git with your own software, best download [Github Desktop](https://desktop.github.com/). When you publish your repo, you must decide whether it should be private or public. Free Github Action ressources are more limited on a private repo but on a public repo everybody can access your files. Perhaps when you first try it out for a real supplement and article use a private repo. You can then also consider a public repo with encrypted input and output.

5. If your replication package has Stata, you need to add a repository secret for Github actions with name `STATA_LIC` that has as content the copied text of your `STATA.LIC` file. For the current set-up, you need a license that works for Stata 17 SE. (*Better* Stata licenses, like Stata 17 MP, or Stata 18 SE should also work.) Make sure that you adhere to the terms of the license, e.g. don't run multiple jobs in parallel if your license only allows single usage. The ability to use Stata in this fashion via Github Actions almost directly builds upon the great work by Lars Vilhuber (see https://aeadataeditor.github.io/posts/2021-11-16-docker)

6. Go to the `Actions` tab on your repository page on Github, click on the `Run Repbox` workflow on the left and then on `Run workflow`.

7. After the workflow has run (green circle if succesful), click on the workflow run and scroll down to see the link to the ZIP file `repbox_results` that you can download and extract.

8. If you want to use a public repository but want to have a little bit of security, you can encrypt the article and supplement by putting the article in the `art` directory and the ZIP of the supplement in the `sup` directory into an encrypted [7zip](https://www.7-zip.org/) `.7z` archive. You need to add the password as a repository secret with name `REPBOX_ENCRYPT_KEY` to your Github Repo. Also change the fields `encyrption` in the `io_config.yml` file for `output`, `art` and `sup` to `true`. (Again see the video tutorial for more details.)

## Using for another Replication Package

After you have set up everything, performing an analysis for another replication package goes faster. Just keep the same repo, change the content of `art` and `sup`. Commit and push the changes to Github, run the workflow and download the results.

## Automating the steps

All the steps can be automated, e.g. with a shell or R script. Useful will be the [Github cli](https://cli.github.com/) command line utility. if you are a data editor, just contact me and I can help you via Zoom.

## The future

Many things need to be done...

- Everything must be more robust.

- Better more comprehensive reports.

- Instead of a single monolithic Docker container, it probably would be better to to have 3 containers. One that manages the repbox analysis, one specific container for the Stata scripts in the reproduction package (in a way that the Stata version can be customized) and one that runs the R scripts in the reproduction package. But it will take some while to implement that.

- General improvements, more features...
