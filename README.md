# carbon-smtp-adapter

A simple SMTP adapter for `luckyframework/carbon` using the great work of ` arcage/crystal-email`

## Usage

```crystal
  require "carbon-smtp-adapter"

  # Recommended to pass your informations about your SMTP connection via ENV
  domain = ENV.fetch("SMTP_MAIL_DOMAIN")
  username = ENV.fetch("SMTP_MAIL_USERNAME")
  password = ENV.fetch("SMTP_MAIL_PASSWORD")
  port = ENV.fetch("SMTP_MAIL_PORT"){ "587" }.to_i

  # Create a new SMTP configuration
  config = EMail::Client::Config.new(domain, port)
  config.use_auth(username, password)
  config.use_tls

  # Settings up your Carbon adapter.
  adapter = Carbon::SMTPAdapter.new(config)

  mail = ... # check the mail object of Carbon API to create a proper email/

  # Send a mail
  adapter.deliver_now(mail)
```

## This is tested?

Not yet. I'm struggling with my time the last months and cannot work as much as I would expect in open source projects.

However, I use it in a production project; if you want to use it, feel free to open issues if you have any questions!