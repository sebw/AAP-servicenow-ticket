# Automate the creation of a ServiceNow Incident with Ansible Automation Platform

This job creates an incident in ServiceNow and displays the INC number.

The tasks connects to the API of ServiceNow, using the Ansible Collection for ServiceNow.

As such, the job template should target a `localhost` machine with `ansible_connection: local`.

A vault contains the secrets:

```yaml
vault_snow_host: https://devABCXYZ.service-now.com                              
vault_snow_user: a-snow-account                                                          
vault_snow_pass: your-password
```

Create a Vault credential with the vault password for the job template to be able to decrypt the vault.

The job can take several parameters that can be overidden:

- short: a short description of the problem
- long: a longer description of the problem
- impact: low, medium or high
- urgency: low, medium or high

Make sure to tick the "Prompt on launch" box for variables.

You can create surveys to take those parameters or implement this job as a step in a workflow when something fails.

## Screenshots

Creation of the job (please note the vault credential)

![](https://raw.githubusercontent.com/sebw/AAP-servicenow-ticket/main/screenshots/1.png)

Creating an incident using a survey (the job can also be called by an external entity or part of a workflow and pass `extra_vars`)

![](https://raw.githubusercontent.com/sebw/AAP-servicenow-ticket/main/screenshots/2.png)

Ticket has been created and we have the incident number

![](https://raw.githubusercontent.com/sebw/AAP-servicenow-ticket/main/screenshots/3.png)

Searching the incident in ServiceNow gives us the short description

![](https://raw.githubusercontent.com/sebw/AAP-servicenow-ticket/main/screenshots/4.png)

The full description shows the short and long description and the urgency and priority that have been specified in the survey

![](https://raw.githubusercontent.com/sebw/AAP-servicenow-ticket/main/screenshots/5.png)

