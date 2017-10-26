# Updating Licenses

Updating Licenses on GitHub is hard, and annoying.

### Relevant npm packages

- [generate-license](https://www.npmjs.com/package/generate-license): Great for generating a license, but not for updating.
- [license-up](https://github.com/sungwoncho/license-up): Goes through each of your repos where you are the owner from the CLI, and updates the year. However, can't be limited to a single organization ([relevant issue](https://github.com/sungwoncho/license-up/issues/3)).
- [repolinter](https://www.npmjs.com/package/repolinter): Check if a license exists for a repository.
- [updater-license](https://www.npmjs.com/package/updater-license): This updater add a LICENSE file or replaces the LICENSE file in the current working directory using a template defined by you in ~/templates/LICENSE (user home on your system), or the generic template in this project's templates directory. It also does insane crazy things like updating Homebrew, because it has an unfortunate alias, or it doesn't work as scoped. For now, not usable.
- [licenser](https://www.npmjs.com/package/licenser): Close, but it automatically grabs authors from `package.json`, which isn't always ideal. It also replaces the year, and doesn't add to it. I opened two issues for this.

### Updating polyglot packages

There are several types of manifests which keep license information.

#### JavaScript
- `package.json`: `"license": "MIT"`. `Licenses` is deprecated.
- `composer.json`: `"license": "MIT"`

#### Ruby
- `*.gemspec`: `spec.license = "MIT"`

#### Perl
- `META.yml`: `license: mit`. [Required by CPAN](https://metacpan.org/pod/Module::Build::API#license).

#### Python
- `setup.py`: `license='MIT License'`

### GitHub endpoints

You can get the license using the new GitHub API at https://developer.github.com/v3/licenses/.

