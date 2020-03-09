# Hands On lab

## Instructions
Create an Ansible role to modify the MOTD. The role should be in version control.

The MOTD should display the message: ip addresses of this host.

If the host's Operating System is RedHat, display the ip address.
If the host's Operating System is Ubuntu, display the ip address and the fictionary stock "WIKI" Opening stock prie on 2018-03-26 using Quandl.

When the role is completed, create a pull request and merge to master.

### Appendix
1. Quandl API Documentation: https://docs.quandl.com/docs/in-depth-usage
2. Dataset: https://www.quandl.com/api/v3/datasets/WIKI/FB/data.json?api_key=rQW6A_tE6Ampfxxyvp-H




curl -s "https://www.quandl.com/api/v3/datasets/WIKI/FB/data.json?start_date=2018-03-26&end_date=2018-03-26&api_key=rQW6A_tE6Ampfxxyvp-H" | jq '.dataset_data.data[][2]'