---
description: >-
  Settings that can be set to apply to all your sheets within a given sheetwork
  project's scope.
---

# Project-level Controls \(sheetwork\_project.yml\)

## Project Name

* `project_name`: holds a string with the name of the project you are running

{% hint style="danger" %}
The project name must correspond to a top-level entry in [profiles.yml](../installation-and-configuration/configuration-authentication/set-up-your-sheetwork-profile.md#how-to-set-up-your-profiles-yml) and there must be a `./sheetwork/google/<project_name>.json` with the credentials corrsponding to the project. See [connection to Google Sheets for more info](../installation-and-configuration/configuration-authentication/connecting-to-google-sheets.md#what-do-you-do-with-the-credential-files)
{% endhint %}

## Objects creation \(tables & schemas\)

### The sheetwork\_project.yml can store the following project-level settings

* `always_create_table` : when set to `true` table objects will be created if they do not exist.
  * `destructive_create_table` : when set to `true`tables will be replaced \(or dropped\) first and their content will be fully overwritten. When set to `false` content will be appended provided the structure of the table has not changed. If that is the case you will likely get a `DatabaseError` telling you that there is a column mismatch.
* `always_create_schema`: when set to `true`  the target schema will first be created if it does not exist. 
* `target_schema` a project-wide default schema in which to create the tables \(can be overriden in the sheets.yml or via CLI\).

### The following controls can be overridden via CLI arguments at runtime

If you do not wish to provide project-level defaults, you will have to make sure you provide flags on the CLI to control object creation. By default, `sheetwork` does not create objects to prevent surprises.

* `--create_table` when passed on the CLI tables will be created if they do not exist.
* `--create_schema` when passed on the CLI schema will be created if they do not exist.
* `--destructive_create_table` will make replace the old target table with the new one \(either via the `replace` command or `drop` and `create` depending on your database\).
* `--schema` provide or override any of the project- or profile- level target schema specifications.

