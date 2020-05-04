# Hands On lab

## Instructions
Create an Ansible role to customize the MOTD(Message of the Day) on Ubuntu and/

1. Remove the default MOTD banner.
2. The MOTD should display the message `Primary Interface IP Address: ip addresses of this host`.
3. Additionally, if the host's Operating System is Debian, display the Primary ip address as well as the fictionary stock "WIKI" Opening price on 2018-03-26 using Quandl API.

```
Primary Interface IP Address:

Opening stock price:
```
5. Optional: If the host's Operating System is RedHat, display the Primary ip address.
```
Primary Interface IP Address:
```

6. When the role is completed, create a pull request.

### Appendix / Guideline
1. The path for MOTD in Ubuntu is `/etc/update-motd.d/10-banner-text`.
2. Quandl API Documentation: https://docs.quandl.com/docs/in-depth-usage
3. Dataset: https://www.quandl.com/api/v3/datasets/WIKI/FB/data.json?api_key=rQW6A_tE6Ampfxxyvp-H
4. All changes should be tracked in version control.
