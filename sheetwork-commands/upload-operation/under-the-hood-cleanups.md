# Under the Hood Cleanups

## What does sheetwork do under the hood?

Sheetwork has a few cleanups backed in that it applies to **column names** as well as to some of the content. For now, the only way to avoid these cleanups to be performed is to run sheetwork in [`--interactive` mode](./#optional-but-mighty-flags), with the exception of [camelCase to snake\_case transformations](under-the-hood-cleanups.md#camelcase-to-snake_case) which you can control in your `sheets.ym` file.

### Column Cleanups

#### CamelCase to snake\_case

{% hint style="info" %}
Particularly handy for databases like Snowflake as this database forces column names to be UPPERCASE.
{% endhint %}

If your google sheet contains columns that look like this `ColumnWithCamelCasing` chances are your database client will make them look like \```COLUMNWITHCAMELCASING```which isn't the prettiest thing... 

Sheetwork will automatically reformat camel cased columns to something that looks like this: `column_with_camel_case` if you have enabled `snake_case_camel: True` in your [sheet configuration](../../usage/sheet-configuration/).

#### Special Characters Removal

Another one that generally upsets your database client are special characters such as `/`, `.` etc. **Sheetwork will convert those to underscores `_`**

#### List of currently replaced characters in column names:

* any character that is not a word \(`^\w\s` regex\), unless it's a whitespace character.
* removes any trailing `_` characters \(at beginning or end of a column\)

{% hint style="info" %}
This looks a little arbitrary? Yes it is... We'd welcome input on this as people start using it on how we can maybe make it more up to the user via configurations. To be continued. If you have ideas feel free to [drop you thoughts in an issue](https://github.com/bastienboutonnet/sheetload/issues/new/choose).
{% endhint %}

#### Columns with Empty Names

**Those are simply dropped**, ingesting it would make it quite unpredictable if you expect to refer to later.

#### Columns are made case insensitive

We lowercase the column names.

### Field/Content Cleanups

We try not to mess with the content much, that's probably more of an ETL process that other tools \(such as [dbt](https://www.getdbt.com/)\) are best suited for. 

For now, we perform the following: 

#### Trailing whitespace

This one is a pretty nefarious thing to have in your data and we couldn't refrain from sanitising it. Any trailing whitespace will be removed. That means spaces **before and after a string.**

#### **Empty Strings**

These are converted to your database equivalent for `NULL`.

