# Deploying a Rails Application to Heroku

### Overview

This clinic walks through the process of deploying a Rails app to Heroku.

We'll start with a sample Rails app that we've cloned from GitHub.

1. `brew install heroku`
2. Make an account on Heroku if you have not already done so

[Deploying a Rails app to Heroku docs](https://devcenter.heroku.com/articles/getting-started-with-rails5#deploy-your-application-to-heroku)

Some notes about your Rails app:

##### Gemfile

Your `Gemfile` should contain this:

```rb
group :production do
  gem "puma"
  gem "rails_12factor"
end
```

`rails_12factor` is a Heroku gem that does 12 different things.

##### `database.yml`

Your `database.yml` file should contain a couple lines for `production`

```
production:
  <<: *default
  database: heroku_clinic_production
  username: heroku_clinic
  password: <%= ENV['HEROKU_CLINIC_DATABASE_PASSWORD'] %>
```

### Deployment!

`heroku create`

Type in `git remote -v` to ensure that an endpoint called `heroku` has been created.
