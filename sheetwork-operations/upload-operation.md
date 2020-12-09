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

#### The No-YAML-way

If you have not configured your sheet in a `sheets.yml` file you'll have to construct the following command:

```text
sheetwork upload --sheet-key <google_sheet_key> --schema sandbox --table my_table --create-table
```

#### You have a sheets.yml configured?

Nice! We like to think this is the best way to experience the full potential of sheetwork. When you have your sheet configured the `upload` operation isn't that much different from the one shown above. If you have set `always_create: true` in your project.yml file your call could be as simple as that. 

```text
sheetwork upload --sheet-name my_google_sheet
```

If you want to override any of the sheet.yml configuration such as target shema and/or if you have not set the `always_create:` argument to true and your table isn't already in your database you can add those arguments on your call like so:

```text
sheetwork upload --sheet-name my_google_sheet --schema production --create-table
```

### Optional but Mighty Flags

What's shown above is the simplest way to run a google sheet upload and most often that's all you'll need.  But here are a series of CLI arguments that might come in handy later on:

* `--sheet-name / -sn` : sheet name as configured in your sheets.yml
* `--dry-run`: when added sheetwork does everything **except** pushing to the database. It's a good way to test that most of the steps will work and saves surprises on your database.
* `--interactive / -i`: runs sheetwork in interactive mode. This mode allows you to get a preview of the data that is loaded from the sheet, choose whether to clean it up, see the result of that and ultimately choose to push it or not to your database.
* `--target / t`: name of the target to use as configured in your `profiles.yml` file

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

