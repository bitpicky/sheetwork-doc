# Using sheets.yml configuration



## How to set up sheet configuration?

The power of sheetwork is that you can make it do a few handy transformations or sanitisation steps, specify where the sheet should land in your database, whether to rename some columns etc.

To do so you create a `sheets.yml` file which can house configurations for as many sheets as you want. 

{% hint style="info" %}
This is really handy when you want to regularly import google sheets and you don't want to have to set up everything through the command line every time. It also works really well if you're collaborating on code via version control environments like **git** as it will serve as documentation in a way, and allow for iterations.
{% endhint %}

