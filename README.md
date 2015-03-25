# ![Orientation][orientation-logo]

[![Build Status][ci-image]][ci]
[![Test Coverage][codeclimate-coverage-image]][codeclimate-coverage]
[![Code Climate][codeclimate-image]][codeclimate]
[![Dependency Status][gemnasium-image]][gemnasium]

## What is Orientation?

![Orientation's Homepage][orientation-homepage]

See [FEATURES](doc/FEATURES.md) for features and benefits.

### Authentication

I originally tried to make Orientation as easy to onboard to as possible for
people in our team. While a huge majority of us had GitHub accounts, not everyone
did. Nor was it realistic to expect non-developers to setup a GitHub account
just to use a documentation tool. We did — however have — company Google Apps
accounts, so this is what I used. I want to enable custom OAuth providers soon.

## Requirements

### Software
- Ruby 2.2.0
- PostgreSQL 9.1
- Python 2.7 (for Pygments)
- Node.js (for Bower)
- Bower

Both Node and Python are available on Heroku if you decide to deploy there,
which means there should not be any issues when deploying or running Orientation
there.

### Services
- AWS S3 bucket for image uploads
- Mandrill account for transactional emails
- Google account for authentication (for now)

## Installation

Almost one step: `rake orientation:install`

Make sure to check the [installation task](lib/tasks/orientation.rake) if
anything strange happens during installation.

Once you're done, pay close attention to the `.env` file that will appear at the
root. It's copied from [`.env.example`](.env.example) and contains all the
environment variables needed to configure Orientation.

Since setting up S3 is a bit tedious, avatar uploads use local file storage in development.
Likewise, OAuth is disabled in development and you will be signed in as whichever
user is returned from `User.first`.

## Deployment

### Required Environment Variables

See [.env.example](.env.example) file. Note that if you host your Orientation
on Heroku you'll need to set those environment variables manually. I recommend
[dotenv-heroku](https://github.com/sideshowcoder/dotenv-heroku) to do this easily
using you local (git-ignored) `.env` file as a canonical source.

## Development

### OAuth in development
In development we cheat around OAuth by simply using `User.first` as the
current user because it's easy and we're lazy. Testing OAuth in dev is
hard.

If you're curious what the OmniAuth hash from Google OAuth 2 looks like [check
this out](doc/OAUTH.md).

[ci]: https://magnum.travis-ci.com/olivierlacan/orientation
[ci-image]: https://magnum.travis-ci.com/olivierlacan/orientation.svg?token=bYo3ib4PCJrDSsNRgsEK&branch=master
[gemnasium]: https://gemnasium.com/olivierlacan/orientation
[gemnasium-image]: https://gemnasium.com/f8cac37fbe557103d2ae38bcc8815f40.svg
[codeclimate]: (https://codeclimate.com/repos/5158ce6d56b102723b001780/feed
[codeclimate-image]: https://codeclimate.com/repos/5158ce6d56b102723b001780/badges/741c4f4d03a1a9e12804/gpa.svg
[codeclimate-coverage]: https://codeclimate.com/repos/5158ce6d56b102723b001780/feed
[codeclimate-coverage-image]: https://codeclimate.com/repos/5158ce6d56b102723b001780/badges/741c4f4d03a1a9e12804/coverage.svg

[orientation-logo]: https://github.com/olivierlacan/orientation/blob/master/public/orientation_logo.png
[orientation-homepage]: https://cloud.githubusercontent.com/assets/65950/6814712/66cb4684-d281-11e4-800c-329726411b7e.png

## License

Orientation is MIT licensed. See [LICENSE](LICENSE) for details.
