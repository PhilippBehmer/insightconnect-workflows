# Description

Search InsightVM for hosts with a particular vulnerability present directly from Microsoft Teams. Receive a message summarizing the vulnerability and all affected assets in a Microsoft Teams channel.

Sample Microsoft Teams command:

`!lookup-vuln-hosts <vulnerability>`

`lookup-vuln-hosts CVE-2019-0708`

# Key Features

* Identify vulnerable hosts
* Share context with team members in the same Microsoft Teams channel

# Requirements

* InsightVM Console URL and account credentials
* [Microsoft Teams](https://insightconnect.help.rapid7.com/docs/microsoft-teams)

# Documentation

## Setup

Import the workflow from the Rapid7 Extension Library and proceed through the Import Workflow wizard in InsightConnect. Import plugins, create or select connections, and rename the workflow as a part of the Import Workflow wizard as necessary.

This workflow leverages insightConnect's Parameters feature. This feature allows variables used multiple times throughout a workflow to be entered once and then referenced throughout the workflow. To begin, select "Parameters" either from the Workflow home page or from the Builder to begin configuration.

There are three parameters you will need to configure in order to complete setup of your workflow:
* `Team Name`:  the Microsoft Teams team name in your environment where the workflow should be triggered and respond
* `Channel Name`:  the Microsoft Teams channel name in your environment where the workflow should be triggered and respond (the channel should exist in the aforementioned team)
* `Max Hosts`: the maximum number of hosts listed per vulnerability (recommended default is 10)
* `Max Vulnerabilities`: the maximum number of returned vulnerabilities (recommended default is 50)

To configure the parameters, select "Parameters" either from the Workflow Control Panel page or from the Workflow Builder. Once configured, workflow setup is complete.
### Usage

*This workflow will only trigger in the channel specified in the Microsoft Teams workflow steps.*

To run the workflow, send a message to the specified Microsoft Teams channel starting with the command `!lookup-vuln-hosts`.

Commands should be in the following format: `!lookup-vuln-hosts <vulnerability>`

`<vulnerability>` in the command can be any InsightVM vulnerability reference including the following:
* KB Number
* CVE ID
* Nexpose ID
* Other references InsightVM knows

For example:
* `!lookup-vuln-hosts bluekeep`
* `!lookup-vuln-hosts CVE-2019-0708`

The workflow will post status updates in the designated Microsoft Teams channel as it runs.

## Technical Details

Plugins utilized by workflow:

|Plugin|Version|Count|
|----|----|--------|
|Rapid7 InsightVM|4.8.1|5|
|Microsoft Teams|3.1.0|8|
|CSV|1.1.5|1|
|Rapid7 Vulnerability & Exploit Database|2.0.3|1|
|Type Converter|1.6.0|3|

## Troubleshooting

_There is no troubleshooting information at this time_

# Version History

* 2.0.0 - Use Workflow Parameters to configure Microsoft Teams team & channel names, max vulnerabilities, and max hosts values (and remove the Settings step) | Update CSV to version 1.1.6 | Update Type Converter to 1.7.0 | Update Type Converter to 1.7.0
* 1.1.0 - Use the automatic extraction functionality instead of Pattern Match step to extract a vulnerability | Remove HTML step | Add max vulnerabilities parameter in Setting step | Remove team name and channel name parameters from Setting step | Improve workflow messaging | Improve documentation | Update screenshots | Update Rapid7 InsightVM to version 4.8.1 | Update Microsoft Teams to version 3.1.0 | Update Type Converter to version 1.6.0
* 1.0.1 - Update to make Microsoft Teams plugin the latest version
* 1.0.0 - Initial workflow

# Links

## References

* [Rapid7 InsightVM](https://www.rapid7.com/products/insightvm)
* [Microsoft Teams](https://insightconnect.help.rapid7.com/docs/microsoft-teams)
