# Introduction

## What is sheetwork?

**sheetwork** is a handy open-source CLI-tool that allows non-coders to ingest Google Spreadsheets directly into their databases with control over data types, renaming, basic data sanitisation etc.

{% hint style="danger" %}
**sheetwork** is still very much in its **early inception** do not use it for production jobs unless you have taken the time to thoroughly test it.

**compatibility** tested and developed on `python >= 3.6`, `Mac OS >= 0.15`. Integration tests are successful on Mac OS, and Ubuntu platform but fails on Windows \(due to an issue with `gspread` --the library we use to connect to GoogleSheets-- accessing  `APPDATA`\). That being said, it has not been properly tested on Windows platforms. Check [how to contribute to the project](https://github.com/bastienboutonnet/sheetwork/blob/dev/nicolas_jaar/CONTRIBUTING.md) if you would like to try it or help.
{% endhint %}

{% hint style="info" %}
**sheetwork** currently only offers support for cloud database [Snowflake](https://www.snowflake.com/). However, its design follows an adapter pattern \(currently in the making\) and can be extended to interact with most databases. Feel free to check how you can [contribute to the project](https://github.com/bastienboutonnet/sheetload).
{% endhint %}

### How to use sheetwork?

#### Quick & "Dirty"

**sheetwork** is as simple and quick to use as it is too write the following line of code

```
$ sheetwork upload --sheet_key 123afakekey11 --schema sandbox --table my_table
```

{% hint style="warning" %}
 Control over the content of your google sheet and how it lands on the database will be limited, and all columns will be materialised on your database as strings.
{% endhint %}

#### sheetwork project & YAML configuration

For maximum control over your content **sheetwork** uses `.yml` files to let you configure operations you might want it to perform on your google sheet such as type casting, renaming, sanitization etc. Here is what a basic `sheets.yml` file looks like:

{% code title="sheets.yml" %}
```bash
sheets:
  - sheet_name: test_sheet
    sheet_key: 123afakekey
    target_schema: sandbox
    target_table: my_google_sheet
    snake_case_camel: True
    columns:
      - name: col_numeric
        datatype: numeric
      - name: col_b
        datatype: varchar
      - name: renamed_col
        identifier: "A long and dirty name"
    excluded_columns: ['to_exclude', 'col_not_in_df_for_fun']
```
{% endcode %}

All it takes to ingest your newly configured sheet is to call it in the command line with the following arguments

```bash
$ sheetwork upload --sheet_name test_sheet
```

**Yep! It's that simple!**

Now of course there's a lot more to it, so we'll see you in another section for sure!

