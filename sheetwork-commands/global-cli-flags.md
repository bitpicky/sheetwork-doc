# Global CLI flags

## Version

The `--version` flag returns information about the currently installed version of sheetwork. If you are connected to the internet, version will also check whether your version is up to date or not

```text
$ sheetwork --version
Sheetwork version: 1.0.0

sheetwork Running v1.0.0
```

### Log Level

The `--log-level` argument followed by, for example, `debug` will set debug level prints to the CLI in addition to `sheetwork_logs/sheetwor_log.log` which always contains **all** log messages.

## Danger Zone

{% hint style="danger" %}
**The following flags should only be used if you have a good reason in mind and might result to unexpected behaviour. Sheetwork is meant to be used within it's own project folder for most cases.**
{% endhint %}

### Profile Dir

The `--profile-dir` flag followed by a full path can override the location of your [profiles.yml](../usage/profile-level-controls-profiles.yml.md) file.

### Project Dir

The `--project-dir` flag followed by a full path can override the location of your [sheetwork\_project.yml](../usage/project-level-controls-sheetwork_project.yml.md) file.

### Full Tracebacks

By default sheetwork shortens the tracebacks to only the most direct errors. If you need full tracebacks because you find that you need to debug something add the `--full-tracebacks` flag to your CLI call.

