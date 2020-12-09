# Sheet-level Controls Reference

## Referencing Sheets

### Sheet Name

This is the human-readable name by which you want to call your sheet. It can be anything you want and has no impact on the table name, nor does it refer to the actual sheet name on google sheets

```yaml
sheets:
  - sheet_name: wow_such_a_cool_sheet_name_9000
    sheet_key: 10J67dhgTRqtI_lm4bf9B02nZu6zu9u9r9h2VABTjRXd
    target_schema: sandbox # this will override the profiles.yml entry
    target_table: bb_test_sheetwork
```

### Sheet Key

This corresponds to the unique identifier of a google sheet. You can find it in the middle of the URL of the sheet when it's loaded in your browser. **This is the only method by which sheetwork identifies the sheet in your google account**.

### Worksheet

Each google sheet can be made of several tabs or \(worksheets\). By default sheetwork will ingest the first sheet available. If you want to target a specific tab you need to provide its name in the field labelled `worksheet:`

```yaml
sheets:
  - sheet_name: wow_such_a_cool_sheet_name_9000
    sheet_key: 10J67dhgTRqtI_lm4bf9B02nZu6zu9u9r9h2VABTjRXd
    worksheet: Sheet2
    target_schema: sandbox # this will override the profiles.yml entry
    target_table: bb_test_sheetwork
```

## Destinations

### Target Schema

You can choose a target schema for each sheet. **NOTE:** you may have configured a profile-wide `target_schema` variable in your [profile.yml](../profile-level-controls-profiles.yml.md). If that is the case, **the sheets.yml entry will have priority \(override\) over that global one**.

### Target Table

This variable controls the **name of the table as it will land on your database** it can absolutely be different from the `sheet_name`, but that is entirely up to you.

### Snake Case Camel

If you set `snake_case_camel` to `true` column names which are `SnakeCased` will first be converted to `camel_case`. This is particularly handy as most databases do not have column names that are case sensitive so you'd potentially end up with a column name that looks like `SNAKECASE` or something like that.



```yaml
sheets:
  - sheet_name: wow_such_a_cool_sheet_name_9000
    sheet_key: 10J67dhgTRqtI_lm4bf9B02nZu6zu9u9r9h2VABTjRXd
    worksheet: Sheet2
    snake_case_camel: true # this will convert camelCased col names to snake_cased ones
```

## Columns Controls

The columns section of the sheets.yml allows you to do some more fine-grained _sanitisation_ as well as control data-type casting.

### Column Data Type casting

You can control the datatype of a column if you want to make sure that it lands in your database in a type other than `varchar` which is the default behaviour.

In the example before for example, `Col_a` is going to be converted into an `integer`  

```yaml
sheets:
  - sheet_name: wow_such_a_cool_sheet_name_9000
    sheet_key: 10J67dhgTRqtI_lm4bf9B02nZu6zu9u9r9h2VABTjRXd
    worksheet: Sheet2
    snake_case_camel: true # this will convert camelCased col names to snake_cased ones
    columns:
      - name: Col_a
        datatype: int
      - name: col_numeric
        datatype: numeric
      - name: col_b
        datatype: varchar
```

### Column Renaming

When `name:` alone is used, sheetwork assumes that you want to refer to the column in sheetwork and your database in same way as it is in the sheet. For example, in the example above you can see that `Col_a` has capitalisation which is likely to the the way in which it appears in the sheet.

This might not always be ideal if the name in the sheet is complicated, or long etc. You can cause sheetwork to **rename** the column by providing an `identifier:` varible which will **refer to the column as it appears in the sheet** and now the `name:` variable can be anything else you like and **importantly**, it will also be **the name of the column in your database.**

```yaml
sheets:
  - sheet_name: wow_such_a_cool_sheet_name_9000
    sheet_key: 10J67dhgTRqtI_lm4bf9B02nZu6zu9u9r9h2VABTjRXd
    worksheet: Sheet2
    snake_case_camel: true # this will convert camelCased col names to snake_cased ones
    columns:
      - name: a_better_column_name
        datatype: int
        identifier: "A not so fun name in the google sheet"
```

{% hint style="warning" %}
**Not all datatypes are currently supported, if you require an "illegal" datatype, the yml validator will let you know. See** [**"What datatype casting do you support"**](../../faq/what-datatype-casting-do-you-support.md) **for more information.** If this doesn't work out for you, feel free to [open an issue](https://github.com/bastienboutonnet/sheetwork/issues) or to reach out on [Discord](https://discord.gg/ETQ3s998)
{% endhint %}

### Excluded Columns

Sometimes you may not want to ingest the entire sheet. You can easily exclude columns from the ingestion process by providing a list to the `excluded_columns` variable

```yaml
sheets:
  - sheet_name: wow_such_a_cool_sheet_name_9000
    sheet_key: 10J67dhgTRqtI_lm4bf9B02nZu6zu9u9r9h2VABTjRXd
    worksheet: Sheet2
    snake_case_camel: true # this will convert camelCased col names to snake_cased ones
    columns:
      - name: a_better_column_name
        datatype: int
        identifier: "A not so fun name in the google sheet"
    excluded_columns: ["col b", "another col"
```

{% hint style="info" %}
Yes, in theory you should be able to do `included_columns` if your list of excludes is too long. That is currently not yet supported but [it's going to happen](https://github.com/bastienboutonnet/sheetwork/issues/144).
{% endhint %}

