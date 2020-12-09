# Basic Configuration



### Basic Configuration

#### Sheet Details

* `sheet_name`: this is the name by which you'll want to refer to your sheet. It can be anything you like and doesn't have to be the google sheet name. We will refer to the sheet using the sheet\_key as it's less error prone
* `sheet_key:` this is a unique key automatically created for every sheet by google. It's easy to spot, when you have your sheet opened, if you look at the URL it will be something like that. In the example below the key is `10JJdwwd_lm4556uwedu4zu5u6r0h2VIDTjRXg` it always follows the `/d/` and precedes the `/edit` part.

```text
https://docs.google.com/spreadsheets/d/10JJdwwd_lm4556uwedu4zu5u6r0h2VIDTjRXg/edit#gid=0
```

* `target_schema:` This one is optional if you set up a `target_schema` in your project file. If you did not, or you want to override the default you can just specify it here!
* `target_table:` This will be the name of the table in which sheetwork will push your data from the sheet.

