# MOTD Exercise

## Instructions
Create an Ansible role to customize the MOTD (Message of the Day).

1. Remove the default MOTD banner, if there is any.
2. If the host's Operating System is CentOS, display the Primary ip address.`Primary Interface IP Address: ip addresses of this host`.

3. Optionally, if the host's Operating System is Debian, display the Primary ip address as well as the fictionary stock "WIKI" Opening price on 2018-03-26 using Quandl API.

```
Primary Interface IP Address:

Opening stock price:
```

4. When the role is completed, create a pull request.

### Appendix / Guideline
1. The path for MOTD for Ubuntu and CentOS are `/etc/update-motd.d` and `/etc/motd` respectively.
2. Quandl API Documentation: https://docs.quandl.com/docs/in-depth-usage
3. Dataset: https://www.quandl.com/api/v3/datasets/WIKI/FB/data.json?api_key=rQW6A_tE6Ampfxxyvp-H
4. All commits and changes should be tracked in version control.
5. An inventory file and an example playbook has been provided in the root directory.
