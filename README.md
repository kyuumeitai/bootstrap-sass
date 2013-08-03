# Bootstrap for Sass

`bootstrap-sass` is an Sass-powered version of [Bootstrap](https://github.com/twbs/bootstrap), ready to drop right into your Sass powered applications.

## Usage

### Rails

In your Gemfile:

```ruby
<<<<<<< HEAD
gem 'sass-rails', '~> 3.2'
gem 'bootstrap-sass', '~> 2.3.2.1'
=======
gem 'sass-rails',   '~> 3.2.3'
gem 'bootstrap-sass', :git => 'git://github.com/thomas-mcdonald/bootstrap-sass.git', :branch => '3'
>>>>>>> 3
```

`bundle install` and restart your server to make the files available.

<<<<<<< HEAD
#### CSS

Import Bootstrap in an SCSS file (for example, `application.css.scss`) to get all of Bootstrap's styles, mixins and variables! We recommend against using `//= require` directives, since none of your other stylesheets will be [able to use](https://github.com/thomas-mcdonald/bootstrap-sass/issues/79#issuecomment-4428595) the awesome mixins that Bootstrap has defined.
=======
## Upstream Converter
>>>>>>> 3

Keeping bootstrap-sass in sync with upstream changes from Bootstrap is an error prone and time consuming manual process.
This branch is specifically concerned with automating that process as much as possible to allow a much faster release cycle.

Upstream changes to the Bootstrap project can now be pulled in using the `convert` rake task.

Here's an example run that would pull down the `3.0.0-wip` branch from the main twbs/bootstrap repo:

    % bundle exec rake 'convert[3.0.0-wip]'

The latest converter script is located [here](https://github.com/thomas-mcdonald/bootstrap-sass/blob/3/tasks/converter.rb) and does the following:

* Converts upstream bootstrap LESS files to its matching SCSS file.
* Copies all upstream JavaScript into `vendor/assets/javascripts/bootstrap`
* Generates a javascript manifest at `vendor/assets/javascripts/bootstrap.js`
* Copies all upstream font files into `vendor/assets/fonts`

<<<<<<< HEAD
`bootstrap-sass` 2.0 now comes with support for Compass, meaning projects that don't use Rails can get in on the fun Bootstrap web.

#### New project

Install the gem and create a new project using the gem.

```console
gem install bootstrap-sass
compass create compass-test -r bootstrap-sass --using bootstrap
```

This will sort a few things out:

* You'll get a starting `styles.scss` ready for your alterations
* You'll get a compiled stylesheet compiled & ready to drop into your application
* We'll also copy the Bootstrap javascripts & images into their respective folders for you, absolutely free of charge! How cool is that?

#### Existing project

Install the gem, add the require statement to the top of your configuration file, and install the extension.

```console
gem install bootstrap-sass
```

```ruby
# In config.rb
require 'bootstrap-sass'
```

```console
compass install bootstrap
```

You'll get the same benefits as those starting from scratch. Radical.

## Configuration
Need to configure a variable or two? Simply define the value of the variable you want to change *before* importing Bootstrap. Sass will respect your existing definition rather than overwriting it with the Bootstrap defaults. A list of customisable variables can be found in the [Bootstrap documentation](http://twitter.github.com/bootstrap/customize.html#variables).

```scss
$btnPrimaryBackground: #f00;
@import "bootstrap";
```

**Note**: It's important that the file you are importing is not named `bootstrap`, since this will cause an import loop. As a general rule, errors are something you should try to avoid.

### Passing multiple values to mixins

Some CSS3 properties take multiple values, such as `box-shadow` or `text-shadow`. To pass multiple values to the Bootstrap mixins, you must escape the values or else the Sass parser will choke on the commas. Here's how to escape the values in Sass:

```scss
.selector {
  @include box-shadow(#{0 2px 5px rgba(0,0,0,.25) inset, 0 -2px 5px rgba(0,0,0,.25) inset});
}
```

### Responsive styling?
As per the Bootstrap project we don't include the responsive styles by default. `@import "bootstrap-responsive";` to get them.

## Versioning
Bootstrap [claims](https://github.com/twitter/bootstrap#versioning) to use SemVer, although this is for values of public API that don't seem to include selectively requiring CSS components (see breaking change 2.0.2 -> 2.0.3). Since many people using bootstrap-sass *do* selectively require CSS components and I consider it part of the public API we can't really follow SemVer without becoming wildly out of sync with the Bootstrap version number, which is confusing for everyone involved. Further releases to bootstrap-sass will therefore have version numbers of the form `2.x.y.z`, where `2.x.y` is the release of Bootstrap we should be compatible with, and `z` is the patch version.

Basically this means you should expect to append a separate patch version to the bootstrap version, which allows our versioning to stay more honest about changes.

### Bundler?

```ruby
gem 'bootstrap-sass', '~> 2.3.2.1'
```

Don't use the standard `~> 2.x.y`. Your apps may break.
=======
This LESS to SCSS conversion is pretty good, but not perfect. So manual fixes to the resulting SCSS will be necessary for now.
Please submit GitHub issues tagged with `conversion` to help track current shortcomings of the conversion process.
>>>>>>> 3

## Who
bootstrap-sass is a project by [Thomas McDonald](https://twitter.com/#!/thomasmcdonald_), with support from [other awesome people](https://github.com/thomas-mcdonald/bootstrap-sass/graphs/contributors).
