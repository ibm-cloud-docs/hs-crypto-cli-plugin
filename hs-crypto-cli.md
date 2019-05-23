---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-22"

keywords: Trusted Key Entry plugin, TKE plugin, CLI plugin, TKE commands

subcollection: hs-crypto

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Trusted Key Entry CLI plug-in reference
{: #tke_cli_plugin}

You can use the Trusted Key Entry (TKE) CLI plug-in to load master key registers before you use the {{site.data.keyword.hscrypto}} instance.
{:shortdesc}

## Installing the TKE CLI plug-in
{: #install-tke-cli-plugin}

To install the TKE CLI plug-in, follow these steps:

1. Install the [{{site.data.keyword.cloud}} CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/cli?topic=cloud-cli-ibmcloud-cli#overview).

  {{site.data.keyword.cloud_notm}} CLI requires Java&trade; SDK 1.7.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`. In the terminal, you are notified when updates to the `ibmcloud` CLI is available. Be sure to keep your CLI up-to-date so that you can use all the available commands and flags.

  To load master key registers to the {{site.data.keyword.hscrypto}} instance, you also need to install the {{site.data.keyword.keymanagementservicefull}} plug-in. For detailed steps, see [Setting up the CLI](/docs/services/hs-crypto/set-up-cli.html).
  {:tip}

2. Install the latest TKE plug-in with the following command:

  ```
  ibmcloud plugin install tke
  ```
  {: codeblock}

  If you are using the Beta instance of ({{site.data.keyword.hscrypto}}, run the `ibmcloud plugin install tke -v 0.0.4` command to get the latest beta version of the TKE plug-in. Do not install later versions of the TKE plug-in.
  {: important}

3. Set the environment variable `CLOUDTKEFILES` on your workstation. Specify a directory where you want master key part files and signature key part files to be created and saved. Create the directory if it does not already exist.

  * On Linux or MacOS, add the following line to the `.bash_profile` file:
     ```
     export CLOUDTKEFILES=<path>
     ```
     {: codeblock}
     
     For example, you can specify the *path* to `/Users/tke-files`.
     
  * On Windows, in **Control Panel**, type `environment variable` in the search box to locate the Environment Variables window. Create a CLOUDTKEFILES environment variable and set the value to the path to the key files. For example, `C:\users\tke-files`.


## TKE CLI plug-in commands
{: #commands_usage}

| Command name | Description | Example|
| -------------| ------------|---------------- |
|tke           |A CLI plug-in to manage crypto units in the IBM Cloud.|`ibmcloud tke`|
|tke mks|Lists EP11 master key parts stored on this workstation.|`ibmcloud tke mks`|
|tke mk-add|Creates and saves a new EP11 master key part.|`ibmcloud tke mk-add`|
|tke mk-rm|Removes an EP11 master key part from this workstation.|`ibmcloud tke mk-rm`|
|tke sigkeys|Lists the signature keys stored on this workstation.|`ibmcloud tke sigkeys`|
|tke sigkey-add|Generates and saves a new signature key.|`ibmcloud tke sigkey-add`|
|tke sigkey-rm|Removes a signature key from this workstation.|`ibmcloud tke sigkey-rm`|
|tke sigkey-sel|Selects the signature key to use to sign commands.|`ibmcloud tke sigkey-sel`|
|tke cryptounits|Displays the crypto units for the current resource group.|`ibmcloud tke cryptounits`|
|tke cryptounit-add|Adds crypto units to the set of crypto units to work with.|`ibmcloud tke cryptounit-add`|
|tke cryptounit-rm|Removes crypto units from the set of crypto units to work with.|`ibmcloud tke cryptounit-rm`|
|tke cryptounit-admins|Lists administrators installed in the selected crypto units.|`cryptounit-admins`|
|tke cryptounit-admin-add|Adds a crypto unit administrator to the selected crypto units.|`ibmcloud tke cryptounit-admin-add`|
|tke cryptounit-admin-rm|Removes a crypto unit administrator from the selected crypto units.|`ibmcloud tke cryptounit-admin-rm`|
|tke cryptounit-compare|Compares configuration settings of the selected crypto units.|`ibmcloud tke cryptounit-compare`|
|tke cryptounit-exit-impr|Exits imprint mode in the selected crypto units.|`ibmcloud tke cryptounit-exit-impr`|
|tke cryptounit-zeroize|Zeroizes the selected crypto units.|`ibmcloud tke cryptounit-zeroize`|
|tke cryptounit-mk|Displays master key registers for the selected crypto units.|`ibmcloud tke cryptounit-mk`|
|tke cryptounit-mk-clrcur|Clears the current master key register.|`ibmcloud tke cryptounit-mk-clrcur`|
|tke cryptounit-mk-clrnew|Clears the new master key register.|`ibmcloud tke mks`|
|tke cryptounit-mk-commit|Commits the new master key register.|`ibmcloud tke cryptounit-mk-commit`|
|tke cryptounit-mk-setimm| Activiates the master key registers.|`ibmcloud tke cryptounit-mk-setimm`|
|tke cryptounit-mk-load|Loads the new master key register.|`ibmcloud tke cryptounit-mk-load`|

For more information on each command, run the following command in the TKE CLI plug-in:

```
ibmcloud tke help <command_name>
```
{:codeblock}
