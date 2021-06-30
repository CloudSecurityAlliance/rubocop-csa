# Maintaining RuboCop CSA

## Table of Contents

1. [Merging Pull Requests](#merging-pull-requests)
1. [Versioning](#versioning)
   1. [Version Naming](#version-naming)
   1. [Releasing a New Version](#releasing-a-new-version)

## Merging Pull Requests

Follow standard PR policy.

## Versioning

### Version Naming

RuboCop CSA uses semantic versioning which can be found at: https://semver.org/

All versions of RuboCop CSA should follow this format: `MAJOR.MINOR.PATCH`

Where:

* MAJOR - Includes backwards **incompatible** changes.
* MINOR - Introduces new functionality but is fully backwards compatible.
* PATCH - Fixes errors in existing functionality (must be backwards compatible).

The changelog and git tags should use `vMAJOR.MINOR.PATCH` to indicate that the
number represents a version of RuboCop CSA. For example, `1.0.0` would become
`v1.0.0`.

For the purposes of changing our RuboCop config, here are some versioning
guidelines:

* DO NOT update major version for config or dependency changes.
* DO update minor version when changing the dependencies in the gemspec.
* DO update patch version when changing the configuration of cops themselves,
  but not changing the dependencies.
* DO NOT release updates for purely metadata changes, such as updating the
  MAINTAINING.md or README.md documentation.

### Releasing a New Version

When it's time to release a new version, you'll want to ensure all the changes
you need are on the main branch and that there is a passing build. Then follow
this checklist and prepare a release commit:

NOTE: `X.Y.Z` and `vX.Y.Z` are given as examples, and should be replaced with
      whatever version you are releasing. See: [Version Naming](#version-naming)

1. Update CHANGELOG.md
   1. Check for any changes that have been included since the last release that
      are not reflected in the changelog. Add any missing entries to the `HEAD`
      section.
   1. Check the changes in `HEAD` to determine what version increment is
      appropriate. See [Version Naming](#version-naming) if unsure.
   1. Replace `## HEAD` with `## vX.Y.Z` and create a new `## HEAD` section
      above the latest version.
1. Update Gem Version
   1. Update `./rubocop-csa.gemspec` to `version = 'X.Y.Z'`
1. Stage your changes and create a commit
   1. `git add -A`
   1. `git commit -m "Release vX.Y.Z"`
   1. `git push`
1. Gem Release
   1. While in the root of this repo:
   1. `gem build`
   1. `gem push rubocop-csa-X.Y.Z.gem`
1. Github Version Tagging
   1. Visit: https://github.com/CloudSecurityAlliance/rubocop-csa/releases/new
   1. Enter in the details
      1. Tag version: "vX.Y.Z"
      1. Release title: "vX.Y.Z"
      1. Describe this release: Copy paste the changelog for this release.
   1. Publish release
