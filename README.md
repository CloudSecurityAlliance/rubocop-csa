# RuboCop CSA

Provides a centralized location for CSA's commonly used RuboCop overrides.

## TODO

- [ ] Add slim linting
- [ ] Investigate multi-line for shoulda matchers (`it { should`...)

## Usage

### Rails Applications

**Gemfile**

```ruby
gem 'rubocop-csa'
gem 'rubocop-faker'
gem 'rubocop-rails'
gem 'rubocop-rspec'
```

**.rubocop.yml**

```yaml
inherit_gem:
  rubocop-csa:
    - config/rails.yml
```

### Ruby Gems

**Gemfile**

```ruby
gem 'rubocop-csa'
gem 'rubocop-faker'
gem 'rubocop-rspec'
```

**.rubocop.yml**

```yaml
inherit_gem:
  rubocop-csa:
    - config/gems.yml
```

### Other Ruby code

**Gemfile**

```ruby
gem 'rubocop-csa'
```

**.rubocop.yml**

```yaml
inherit_gem:
  rubocop-csa:
    - config/default.yml
```
