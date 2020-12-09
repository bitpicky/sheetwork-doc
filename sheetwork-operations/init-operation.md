# sheetwork init

The `init` operation is a nice little helper that allows you to set up a new `sheetwork` project with minimal effort. It takes care of setting up the following:

* your project folder \(along with the `sheetwork_project.yml` file and some useful defaults\)
* your credentials files:
  * this means creating a `~/.sheetwork` folder
  * placing a `/google/<project_name>.json` in which you can write your google auth credentials
  * and creating a `profiles.yml` file where you can declare your profiles and database credentials.

Basically making the [configuration](../installation-and-configuration/untitled/) steps a little bit easier to work with

### Setting up a project from scratch

`sheetwork init` can help you start a project entirely from scratch on your local machine and can be used as follows:

1. navigate to the folder in which you want to set up your project `cd /path/to_where_your_project_should_live`
2. if you are using `sheetwork` in a virtual environment, don't forget to activate it first
3. `sheetwork init --project-name my_awesome_sheetwork_project`

If the `init` operation completed successfully you should see the following:

```text
      / __/ /  ___ ___ / /__    _____  ____/ /__
     _\ \/ _ \/ -_) -_) __/ |/|/ / _ \/ __/  '_/
    /___/_//_/\__/\__/\__/|__,__/\___/_/ /_/\_\
    
Alright let's get to work 

❤️ Taking peanut butter and jelly out of the cupboard 🍇
Your new sheetwork project "sheetwork" has been created ✨.

Here is what happened behind the scenes:
~/your/path/my_awesome_sheetwork_project was created.

- Inside that project, we created "sheetwork_project.yml" containing the bare essentials to get you started.
- An empty google credentials file was dropped in /Users/bboutonnet@tripactions.com/.sheetwork/google and we called it my_awesome_sheetwork_project.json
- If it was your first time setting up sheetwork on your machine, we also created a profiles.yml file

What you need to do now:
- Fill up your profiles.yml file. You can access it by running the following command:
      open ~/.sheetwork

For help on how to fill your profiles.yml file head over to: 
https://bastienboutonnet.gitbook.io/sheetwork/installation-and-configuration/untitled/set-up-your-sheetwork-profile

You will need to fill up the my_awesome_sheetwork_project.json file with your google credentials key. 
For help see: 
https://bastienboutonnet.gitbook.io/sheetwork/installation-and-configuration/untitled/connecting-to-google-sheets

Optionally:
You might want to change some defaults in your /Users/bboutonnet@tripactions.com/Documents/repos/tripactions/data_etl/snowflake_importers/sheetwork/sheetwork.yml file. For help: 
https://bastienboutonnet.gitbook.io/sheetwork/installation-and-configuration/untitled/set-up-your-sheetwork-project

You might want to configure a sheet to import in your sheets.yml file. For help: 
https://bastienboutonnet.gitbook.io/sheetwork/usage/sheet-configuration

```

As you can see from the instructions, you will have a few things to do such as:

* set up the content of your `profiles.yml` files with your database credentials and [google user service account.](../installation-and-configuration/untitled/connecting-to-google-sheets.md)
* place your google auth credentials in the `/google/my_awesome_sheetwork_project.json` file that you obtained via the [following steps](../installation-and-configuration/untitled/connecting-to-google-sheets.md)

### Setting up credentials only in case your sheetwork project was created manually or lives on a shared repository

In the case where you share a repo with someone else or an organisation, chances are the sheetwork project was already created and contains sheets in the `sheets.yml` file or the project's folder. **However, if you have never used sheetwork on your machine or never worked on that project** you probably wont have the [credentials files set up already.](../installation-and-configuration/untitled/)

In that case you will want to use the `init` task with the flag `--force-credentials-folders` otherwise `init` will tell you that your project is already created and that nothing will happen.

1. navigate to the folder in which you want to set up your project `cd /path/to_where_your_project_should_live`
2.  If you run `sheetwork` in a virtual environment, make sure you activate it first.
3. `sheetwork init --project-name my_awesome_sheetwork_project --force-credentials-folders`

If the `init` operation ran successfully you should see the following message:

```text
           ______           __                  __
          / __/ /  ___ ___ / /__    _____  ____/ /__
         _\ \/ _ \/ -_) -_) __/ |/|/ / _ \/ __/  '_/
        /___/_//_/\__/\__/\__/|__,__/\___/_/ /_/\_\

Alright let's get to work
❤️ Taking peanut butter and jelly out of the cupboard 🍇
sheetwork already exists, moving on to credential files.

Alright! Your credential and profile files have been creeated ✨

What you need to do now:

- Fill up your profiles.yml file. You can access it by running the following command:

    open ~/.sheetwork

- For help on how to fill your profiles.yml file head over to:
    https://bastienboutonnet.gitbook.io/sheetwork/installation-and-configuration/untitled/set-up-your-sheetwork-profile

- You will need to fill up the my_awesome_sheetwork_project.json file with your google credentials key. For help see:
    https://bastienboutonnet.gitbook.io/sheetwork/installation-and-configuration/untitled/connecting-to-google-sheets
```

As you can see from the instructions, you will have a few things to do such as:

* set up the content of your `profiles.yml` files with your database credentials and [google user service account.](../installation-and-configuration/untitled/connecting-to-google-sheets.md)
* place your google auth credentials in the `/google/my_awesome_sheetwork_project.json` file that you obtained via the [following steps](../installation-and-configuration/untitled/connecting-to-google-sheets.md)

**Et voila! You're all set**

