# Running sheetwork outside of sheetwork project folders

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

