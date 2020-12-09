# Column Operations & Advanced Controls



## Column Transformations

Sheetwork can perform a series of transformation on your columns. You'll set these up by creating a new `columns` block in your yml as you'll see below

### Data type casting

By default, everything that comes from a Google Sheet will be loaded as a **string**. But you might not want it to land in your database as a string. Here comes column-based casting! Building on the previous example here's what you could do:

```yaml
sheets:
  - sheet_name: test_sheet
    sheet_key: 10JJdwwd_lm4556uwedu4zu5u6r0h2VIDTjRXg
    target_schema: sandbox
    target_table: my_google_sheet
    # create a new columns block
    columns:
      - name: column_a # name of the column in your sheet
        datatype: int
```

#### Supported Data Types

Currently supported data types are:

```text
int: integer
numeric: decimals and other kinds of non-whole number (precision 38,18)
varchar: for strings
date: for dates
boolean: for True False
timestamp: for a datetime object
```

### Column Renaming

This one is fun, it's not uncommon that your google sheet might contain a name that doesn't fit in your database or that is not up to your conventions. You can rename if easily as follows:

```yaml
sheets:
  - sheet_name: test_sheet
    sheet_key: 10JJdwwd_lm4556uwedu4zu5u6r0h2VIDTjRXg
    target_schema: sandbox
    target_table: my_google_sheet
    # create a new columns block
    columns:
      - name: column_a # name of the column in your sheet
        datatype: int
        identifier: "An AwkwardlyNamed Column Gosh that is ugly"
```

The `identifier:` field should be the exact copy of the Google Sheet column you want to rename. That is why we store it between `"` the `name:` field becomes the way you'll refer to the new column from now on. When no `identifier` is provided name will need to be the exact column in the google sheet.

## Column Exclusion

It's not uncommon for google sheets to contain a lot more columns than you'd want. That's where `exclude_colums:` comes in handy! You can list as a many columns as you want to exclude from the import by adding a list of columns as shown below. 

```yaml
sheets:
  - sheet_name: test_sheet
    sheet_key: 10JJdwwd_lm4556uwedu4zu5u6r0h2VIDTjRXg
    target_schema: sandbox
    target_table: my_google_sheet
    # create a new columns block
    columns:
      - name: column_a # name of the column in your sheet
        datatype: int
        identifier: "An AwkwardlyNamed Column Gosh that is ugly"
    excluded_columns: ['Bad COlumn', 'another bad one I do not want']
```

## Column Name Formatting

### Not a fan of CamelCase?

For whatever reason, you might want to convert those CamelCased columns into snake\_cased columns, `snake_case_camel` got your back!

{% hint style="info" %}
In fact Snowflake imposes an ALL\_CAPS convention on its column name. This means that ingesting the following column "CamelCasesCol" would end up in your database as this ugly, unreadable thing: **CAMELCASESCOL** 🤮
{% endhint %}

```yaml
sheets:
  - sheet_name: test_sheet
    sheet_key: 10JJdwwd_lm4556uwedu4zu5u6r0h2VIDTjRXg
    target_schema: sandbox
    target_table: my_google_sheet
    # create a new columns block
    columns:
      - name: column_a # name of the column in your sheet
        datatype: int
        identifier: "An AwkwardlyNamed Column Gosh that is ugly"
    excluded_columns: ['Bad COlumn', 'another bad one I do not want']
    snake_case_camel: True
```

