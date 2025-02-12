# Mailtrap Docker Image

Catch all mail and display it in roundcube interface.

![picture 2](images/1b0084636c5739b018bc914ad751bece14bb8e9cb043cc05e625515bcfa658aa.png)  

# Usage

## Start Mailtrap

    $ docker run -d --name=mailtrap -p 80:80 eaudeweb/mailtrap

## Send email

    $ docker run -it --link mailtrap alpine:3.6 sh

      $ telnet mailtrap 25
      helo example.com
      mail from: me@example.com
      rcpt to: you@example.com
      data
      Subject: Hello from me
      Hello You,

      This is a test.

      Cheers,
      Me
      .
      quit

## See email via Mailtrap Web UI:

* http://localhost

## Default login:

* **Username:** `mailtrap`
* **Password:** `mailtrap`

## Customisations:

Set environment variables

* `MT_USER` - mailbox user, default mailtrap
* `MT_PASSWD` - mailbox user password, default mailtrap
* `MT_MAILBOX_LIMIT` - mailbox limit in bytes, default 51200000
* `MT_MESSAGE_LIMIT` - message limit in bytes, default 10240000

and recreate the container.

## Testing the image locally

```
sudo docker build -t florentgn/mailtrap:test .
sudo docker-compose up
```
