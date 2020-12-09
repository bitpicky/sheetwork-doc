# Connecting to Google Sheets

{% hint style="warning" %}
The Google Developer Console UI changes often, so it may be different that what is explained below. If that is the case, feel free to [submit an issue](https://github.com/bastienboutonnet/sheetwork/issues) or reach out on our [discord server](https://discord.gg/2gwH79) and we'll get this page a lift.
{% endhint %}

## Gspread & OAuth

**sheetwork** interacts with Google Spreadsheet via the [gspread](https://gspread.readthedocs.io/en/latest/) package/API. While you do not need to install it \(it has been taken care of earlier when you installed sheetwork via pip\), you will need to make sure you have **enabled API Access for your project on the Google Developer Platform**.

### Enable API Access 

There are a number of ways in which you can set/get those. The easiest is probably to use **Signed Credentials**

![](../../.gitbook/assets/screenshot-2020-04-12-at-18.12.02.png)

* Head to [Google Developers Console](https://console.developers.google.com/project) and create a new project \(or select an existing one\)
* Hit the menu and head to "API & Services &gt; Library"
* search for "Google Drive API", hit it and click "Enable It"
* back to the menu above, or search for "Sheets API", hit it and click "Enable It"

### Using a Service Account

* Make sure you enable API access \(see above\)
* Go to "APIs & Services &gt; Credentials"
* Hit "Create Credentials". Follow the instructions.
* At some point you will be prompted to "Create a key". Do it and choose ".json" as the output.
* A download will be initiated. If you open it, it will look something like you see below. Check the last section of this page to see what to do with that file.

```bash
{
  "type": "service_account",
  "project_id": "blahsdasda123123123",
  "private_key_id": "s44i84737482234234",
  "private_key": "-----BEGIN PRIVATE KEY-----n",
  "client_email": "username@somestuff.iam.gserviceaccount.com",
  "client_id": "12312312314134123123123123",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://oauth2.googleapis.com/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/username@somestuff.iam.gserviceaccount.com"
}
```

### Using an End User OAuth Client ID \(New in 1.0.1\)

If you use Google Sheets inside of an organisation and want to make sure that you access sheets on behalf of **your** user you can use this authentication method. When you use this method, sheetwork will ask the end user to grant access to the sheet's data.

1. Enable API access for a project \(See above\)
2. Go to "API & Services" &gt; "Oauth Consent Screen". Click "Configure Consent Screen". Follow the instructions on the screen. You probably don't really need to change much from the defaults other than giving your application a name, which in that case could be `sheetwork` you like really.
3. Go to "API & Services" &gt; "Credentials", Click the "Create Credentials" button **at the top** then select "OAuth client ID".
4. Select "Desktop app" from the dropdown, give a name to your credentials \(anything you like\) and click "Create". Make sure you hit "OK" in the "OAuth client created" popup that may come up.
5. Download the credentials you just created by clicking the "Download JSON" button in "OAuth 2.0 Client IDs"
6. Check the section below.

### What do you do with the credential files?

**sheetwork** expects you to place your credentials file in a specific location:

```bash
$ mkdir ~/.sheetwork/google
```

Rename your file to **correspond to your sheetwork project name**. In the previous step we chose to call it `my_sheetwork_project` so in that case your file should be renamed `my_sheetwork_project.json`

Move your renamed file to the folder we created two steps above.

Next, we'll set up your `profile.yml` file which contains: a link to your google credentials as well as your database credentials.



