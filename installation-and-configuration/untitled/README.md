# Configuration

## What is a sheetwork project?

A sheetwork project is a simple `.yml` file that contains some basic information about a collection of sheets you might want to import. It can be located anywhere on your disk but we advise making **one folder per project**

### Create your \`sheetwork\_project.yml\` file

* First make a project folder, we'll call this one `my_sheetwork_project` and we'll put it in your home directory but feel free to put it anywhere that makes sense for you:

```bash
# create a directory
mkdir ~/my_sheetwork_project/
# create an empty sheetwork_project.yml file
touch ~/my_sheetwork_project/sheetwork_project.yml
```

Now open this file in your editor of choice and configure it as follows:

```bash
name: 'my_sheetwork_project' # the name can be anything of your choosing
target_schema: 'sandbox' # optional default schema where you want your sheets to land

# if true, tables will always be created, you can set it to False
# if you would like to control this on every run (check out Running Sheetwork 
# for more info
always_create: true 
```

That's it! Next, we'll set up your connection to the google spreadsheet API

