# Atom Handler

atom:// URL handler for Atom editor on OSX

## Installation

- Download the latest release [(atom-handler.app.zip)](https://github.com/WizardOfOgz/atom-handler/releases/download/1.0.0/atom-handler.app.zip) and unzip it.
- Move atom-handler.app into your */Applications* directory.
- Open the application which will register the handler and exit immediately.

## Usage

Atom Handler will handle URLs which match the [TextMate URL scheme](http://blog.macromates.com/2007/the-textmate-url-scheme/) and take the following format:

`atom://open?url=file://<file>[&line=<line>[&column=<column>]]`

Opening a URL with this format will open the given file in the Atom editor and place the cursor at the beggining of the line number (if given). Note that the column option does not seem to be supported by the Atom command line utility. If a column is given then Atom simply ignores it. The option is supported for compatibility with TextMate and Sublime Text URLs.

### Examples:
- `atm://open?url=file:///path/to/other&line=42`
- `atm://open?url=file:///path/to/file&line=42&column=7`

These URLs may be opened from a browser or from the command line using the system `open` command.

## Integrating with BetterErrors

Install BetterErrors in your Rails application and add the following code to an initializer (or any other location where it will be executed when your application is loaded.)

```ruby
if defined? BetterErrors
  BetterErrors.editor = proc do |full_path, line|
    "atm://open?url=file://#{full_path}&line=#{line}"
  end
end
```

## License

Atom Handler is released under the [BSD 3-Clause license](https://github.com/WizardOfOgz/atom-handler/blob/master/LICENSE).
