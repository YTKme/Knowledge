# Email Install (Self Host)

## Table of Content

- [Install](#install)
  - [Domain Name System (DNS)](#domain-name-system-dns)
- [Configure](#configure)
  - [Cloudflare](#cloudflare)
- [Reference](#reference)

## Install

### Domain Name System (DNS)

## Configure

### Cloudflare

- Navigate to [CLOUDFLARE](https://www.cloudflare.com/) and [Log in](https://dash.cloudflare.com/login) to the [Account home](https://dash.cloudflare.com/) (Dashboard) page.
- Select the domain (example.com) from the **Domains** tab for configuration.\
- On the left navigation, select **DNS**.

#### DNS Records

- Click **Add record** from the **DNS management** section.
- Add a record for the mail server itself.
    - Type: `A`
    - Name: `mail`
    - IPv4 address: `YOUR_SERVER_IP`
    - Proxy status: `DNS only`
    - TTL: `Auto`
- Add a record alias for the mail server.
    - Type: `CNAME`
    - Name: `smtp` (`autoconfig`)
    - Target: `mail.example.com`

## Reference

- [How to Host Your Own Email Server (for free)](https://www.youtube.com/watch?v=8G93NVWkXZk)
- [Mailcow Setup Guide 2025 – Self Host a Secure Mailserver with Docker & Nginx on Linux!](https://www.youtube.com/watch?v=rylCQdx3di8)
