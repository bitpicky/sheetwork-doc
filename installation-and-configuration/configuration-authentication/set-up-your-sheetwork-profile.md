# Set up your sheetwork profile

## What is the sheetwork profile?

Your sheetwork profile is a `.yml` file which holds a reference to your sheetwork project, a link to your google credential file \(which we set up earlier\) and your database credentials

### How to set up your profiles.yml?

In the very first step, we created a `.sheetwork` folder in your home directory in which we created a `/google` folder to house your google credentials. Now is the time to create your `profiles.yml`

```bash
# navigate to your sheetwork folder
cd ~/.sheetwork
# create an empty profiles.yml file
touch profiles.yml
```

Open `profiles.yml` in your editor of choice and configure it as follows:

#### Snowflake Connection

{% hint style="info" %}
At the moment **sheetwork** only supports Snowflake. More database support to come depending on open-source contribution.
{% endhint %}

```yaml
profiles:
  # first entry correspond to your project name.
  my_sheetwork_project:
    # specify a default target profile to use if you want. I called mine "dev"
    target: dev
    # outputs contains one "block" per target profile
    outputs:
      dev:
        db_type: snowflake
        account: <your_snowflake_account>
        user: <your_username>
        password: <your_password>
        role: <your_role>
        database: <a_target_database_in_your_account>
        warehouse: <warehouse_to_use>
        schema: <default_schema_for_your_target>
        guser: <your_google_API_client_email>
```

{% hint style="warning" %}
**guser**: you can find this in your google credentials json file in the **client\_email** field.
{% endhint %}

That's it! You're all set up!

