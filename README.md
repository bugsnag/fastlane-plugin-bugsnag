<div align="center">
  <a href="https://www.bugsnag.com/">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://assets.smartbear.com/m/3dab7e6cf880aa2b/original/BugSnag-Repository-Header-Dark.svg">
      <img alt="SmartBear BugSnag logo" src="https://assets.smartbear.com/m/3945e02cdc983893/original/BugSnag-Repository-Header-Light.svg">
    </picture>
  </a>
  <h1>Fastlane Plugin</h1>
</div>


Add `bugsnag` as a plugin in your configuration:

```
fastlane add_plugin bugsnag
```

Then add the `upload_symbols_to_bugsnag` action to your lane:

```ruby
lane :refresh_dsyms do
  download_dsyms(version: "1.4.2.1")     # Download dSYM files from App Store Connect
  upload_symbols_to_bugsnag              # Upload them to Bugsnag
  clean_build_artifacts                  # Delete the local dSYM files
end
```

Common options:

* `api_key`: The API key associated with the project. Informs Bugsnag which project
  the dSYMs should be applied to.
* `dsym_path`: A path or array of paths for directories containing \*.dSYM files
  or a single \*.zip file to upload. If unspecified, the default behavior is to
  upload the zip files retrieved by a prior invocation of
  [`download_dsyms`](https://docs.fastlane.tools/actions/#download_dsyms), or
  any .dSYM files within the current directory.
* `upload_url`: The URL of the server receiving symbol files. Update this value
  if you are using a private instance of Bugsnag
* `config_file`: The path to the project's Info.plist. Set this value if your configuration file
  is not automatically detected.

View usage additional usage information and options by running:

```shell
fastlane action upload_symbols_to_bugsnag
```

For more information, take a look at the docs 
[using the Fastfile plugin](https://docs.bugsnag.com/build-integrations/fastlane/).

Check out the [example `Fastfile`](fastlane/Fastfile) to
see how to use this plugin.  Try it by cloning the repo, running `fastlane
install_plugins` and `bundle exec fastlane test`.

If you have trouble using plugins, check out the [Plugins
Troubleshooting](https://docs.fastlane.tools/plugins/plugins-troubleshooting/)
guide.

## License

This module is free software released under the MIT License. See [LICENSE.txt](LICENSE.txt) for details.

