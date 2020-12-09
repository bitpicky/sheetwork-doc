---
description: Get your Google sheet into your Database
---

# sheetwork upload

## sheetwork upload

Upload does what it says on the tin, it uploads a google sheet to your database.

### How to run sheetwork upload?

Sheetwork prefers to be ran from the folder where your `sheetwork_project.yml` file resides. We'll touch on another way to do that in a later section but for now:

* open a terminal window
* activate the virtual environment in which you have set up sheetwork
* navigate to your sheetwork project folder

```text
cd ~/my_sheetwork_project
```

Then follow one of the methods below that fits your needs and setup.

#### The No-YAML-way \(full CLI control\)

If you have not configured your sheet in a `sheets.yml` file you'll have to construct the following command:

```text
sheetwork upload --sheet-key <google_sheet_key> --schema sandbox --table my_table --create-table
```

#### You have a sheets.yml configured?

Nice! We like to think this is the best way to experience the full potential of sheetwork. When you have your sheet configured the `upload` operation isn't that much different from the one shown above. If you have set `always_create_table: true` in your [sheetwork\_project.yml](../../installation-and-configuration/configuration-authentication/set-up-your-sheetwork-profile.md) file your call could be as simple as that. 

```text
sheetwork upload --sheet-name my_google_sheet
```

If you want to override any of the sheet.yml configuration such as target schema, whether to create your objects etc you can use the following CLI arguments.

## Running sheetwork outside of sheetwork project folders

{% hint style="danger" %}
This is not the preferred way to run Sheetwork. You will have to make sure you are referring to the right directories and be able to understand potentially strange error messages.
{% endhint %}

Although this is not the preferred usage, you might want the option of running sheetwork from anywhere on your disk. This comes in handy if you're running upload jobs on a scheduler machine and you do not want to complicate your job call with `cd <your_sheeload_project>` type of calls.

### Directory Flags

You can use directory flags and provide paths to the set of necessary files for sheetwork.

* `--sheet-config-dir` : absolute path pointing to your `sheets.yml`
* `--profile-dir`: absolute path pointing to your `profiles.yml` file.
* `--project-dir`: absolute path pointing to your `sheetwork_project.yml` file

### CLI Call will look like this

```text
sheetwork upload --sheet-name test_sheet --sheet-configdir /path/to/sheet_config 
```

