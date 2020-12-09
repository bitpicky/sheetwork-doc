# upload CLI reference

### Sheet Name

The `--sheet-name/-sn` argument followed by the name of the sheet in your [sheets.yml](../../usage/sheet-configuration/) controls which sheet sheetwork will upload to your database.

### Interactive

The `--interactive/-i` mode kicks in an interactive flow where you can preview the data as well as some clean up operations

{% hint style="warning" %}
This flow isn't the most fun as of yet, we need to give it some love.
{% endhint %}

### Target

The `--target/-t` argument followed by the name of your target in the [profiles.yml](../../usage/profile-level-controls-profiles.yml.md) can control which target to use. If not provided, sheetwork will use the default target configured in your [sheetwork\_project.yml](../../usage/project-level-controls-sheetwork_project.yml.md) file.

### Create Table

The `--create-table` flag will ensure that your table is first created. See **Destructive Create Table** section for more control over this flag

### Create Schema

The `--create-schema` flag will ensure that your target schema is first created if it does not exist.

### Destructive Create Table

When used the `--destructive-create-table` flag will force your target table to be created. **This means that if it already exists it will be replaced by the new table you're about to upload**. If left out from the command like and/or set to `false` in your [sheetwork\_project.yml](../../usage/project-level-controls-sheetwork_project.yml.md) the table will **not** be created and the **content will be appended** if the target table and the one you're about to push have the same structure.

### Optional but Mighty Flags

What's shown above is the simplest way to run a google sheet upload and most often that's all you'll need.  But here are a series of CLI arguments that might come in handy later on:

* `--sheet-name / -sn` : sheet name as configured in your sheets.yml
* `--dry-run`: when added sheetwork does everything **except** pushing to the database. It's a good way to test that most of the steps will work and saves surprises on your database.
* `--interactive / -i`: runs sheetwork in interactive mode. This mode allows you to get a preview of the data that is loaded from the sheet, choose whether to clean it up, see the result of that and ultimately choose to push it or not to your database.
* `--target / t`: name of the target to use as configured in your `profiles.yml` file

