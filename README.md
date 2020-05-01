# Hands On lab

## Instructions
Create an Ansible role to customize the MOTD(Message of the Day). The role should be in version control.

1. Remove the default MOTD banner. The MOTD should display the message: ip addresses of this host.
2. MOTD for Ubuntu is located on /etc/update-motd.d/10-banner-text.

Optional: If the host's Operating System is RedHat, display the Primary ip address.
```
Primary Interface IP Address:
```

If the host's Operating System is Debian, display the Primary ip address and the fictionary stock "WIKI" Opening price on 2018-03-26 using Quandl API.

```
Primary Interface IP Address:

Opening stock price:
```

When the role is completed, create a pull request.

### Appendix
1. Quandl API Documentation: https://docs.quandl.com/docs/in-depth-usage
2. Dataset: https://www.quandl.com/api/v3/datasets/WIKI/FB/data.json?api_key=rQW6A_tE6Ampfxxyvp-H
