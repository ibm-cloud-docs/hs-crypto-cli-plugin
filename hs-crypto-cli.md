---

copyright:
  years: 2018, 2020
lastupdated: "2020-09-29"

keywords: Hyper Protect Crypto Services, Trusted Key Entry plug-in, cloud tke, TKE plug-in, CLI plug-in, TKE commands, Cloud TKE reference

subcollection: hs-crypto-cli-plugin

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} Trusted Key Entry CLI
{: #tke_cli_plugin}

You can use the {{site.data.keyword.cloud}} Trusted Key Entry (TKE) command-line interface (CLI) plug-in to load the master key before you use the {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} instance.
{:shortdesc}

## Installing the {{site.data.keyword.cloud_notm}} TKE CLI plug-in
{: #install-tke-cli-plugin}

To install the TKE CLI plug-in, follow these steps:

1. Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started){: external}.

  {{site.data.keyword.cloud_notm}} CLI requires Java&trade; SDK 1.7.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`. In the terminal, you are notified when updates to the `ibmcloud` CLI are available. Be sure to keep your CLI up-to-date so that you can use all the available commands and flags.

  To load master key registers to the {{site.data.keyword.hscrypto}} instance, you also need to install the {{site.data.keyword.keymanagementservicefull}} plug-in. For detailed steps, see [Setting up the CLI](/docs/hs-crypto?topic=hs-crypto-set-up-cli).
  {: tip}

2. Install the latest TKE plug-in with the following command:

  ```
  ibmcloud plugin install tke
  ```
  {: pre}

3. Set the environment variable `CLOUDTKEFILES` on your workstation. Specify a directory where you want master key part files and signature key part files to be created and saved. Create the directory if it does not exist.

  * On the Linux&trade; operating system or MacOS, add the following line to the `.bash_profile` file:

     ```
     export CLOUDTKEFILES=<path>
     ```
     {: pre}

     For example, you can specify the *path* to `/Users/tke-files`.

  * On the Windows&trade; operating system, in **Control Panel**, type `environment variable` in the search box to locate the Environment Variables window. Create a CLOUDTKEFILES environment variable and set the value to the path to the key files. For example, `C:\users\tke-files`.


## {{site.data.keyword.cloud_notm}} TKE CLI plug-in commands
{: #commands_usage}

| Command name | Description | Example |
| ------------ | ----------- | ------- |
| `tke` | A CLI plug-in to manage crypto units in the IBM Cloud. | `ibmcloud tke` |
| `tke cryptounit-add` | Adds crypto units to the set of crypto units to work with. | `ibmcloud tke cryptounit-add` |
| `tke cryptounit-admin-add` | Adds a crypto unit administrator to the selected crypto units. | `ibmcloud tke cryptounit-admin-add` |
| `tke cryptounit-admin-rm` | Removes a crypto unit administrator from the selected crypto units. | `ibmcloud tke cryptounit-admin-rm` |
| `tke cryptounit-admins` | Lists administrators installed in the selected crypto units. | `cryptounit-admins` |
| `tke cryptounit-compare` | Compares configuration settings of the selected crypto units. | `ibmcloud tke cryptounit-compare` |
| `tke cryptounit-exit-impr` | Exits imprint mode in the selected crypto units. (**Deprecated.** Use `cryptounit-thrhld-set` instead.) | `ibmcloud tke cryptounit-exit-impr` |
| `tke cryptounit-mk` | Displays master key registers for the selected crypto units. | `ibmcloud tke cryptounit-mk` |
| `tke cryptounit-mk-clrcur` | Clears the current master key register. | `ibmcloud tke cryptounit-mk-clrcur` |
| `tke cryptounit-mk-clrnew` | Clears the new master key register. | `ibmcloud tke cryptounit-mk-clrnew` |
| `tke cryptounit-mk-commit` | Commits the new master key register. | `ibmcloud tke cryptounit-mk-commit` |
| `tke cryptounit-mk-load` | Loads the new master key register. | `ibmcloud tke cryptounit-mk-load` |
| `tke cryptounit-mk-rotate` | Promotes the master key in the new master key register to the current master key register after rewrapping root keys and encryption keys in the key management keystore. | `ibmcloud tke cryptounit-mk-rotate` |
| `tke cryptounit-mk-setimm` | Does set immediate on the master key registers. | `ibmcloud tke cryptounit-mk-setimm` |
| `tke cryptounit-rm` | Removes crypto units from the set of crypto units to work with. | `ibmcloud tke cryptounit-rm` |
| `tke cryptounit-thrhld-set` | Sets the signature thresholds for the selected crypto units. | `ibmcloud tke cryptounit-thrhld-set` |
| `tke cryptounit-thrhlds` | Displays signature thresholds for the selected crypto units. | `ibmcloud tke cryptounit-thrhlds` |
| `tke cryptounit-zeroize` | Zeroizes the selected crypto units. | `ibmcloud tke cryptounit-zeroize` |
| `tke cryptounits` | Displays the crypto units for the current resource group. | `ibmcloud tke cryptounits` |
| `tke mk-add` | Creates and saves a new EP11 master key part. | `ibmcloud tke mk-add` |
| `tke mk-rm` | Removes an EP11 master key part from this workstation. | `ibmcloud tke mk-rm` |
| `tke mks` | Lists EP11 master key parts that are stored on this workstation. | `ibmcloud tke mks` |
| `tke sigkey-add` | Generates and saves a new signature key. | `ibmcloud tke sigkey-add` |
| `tke sigkey-rm` | Removes a signature key from this workstation. | `ibmcloud tke sigkey-rm` |
| `tke sigkey-sel` | Selects the signature keys to use to sign commands. | `ibmcloud tke sigkey-sel` |
| `tke sigkeys` | Lists the signature keys that are stored on this workstation. | `ibmcloud tke sigkeys` |
| `tke help`, `tke h` | Shows help. | `ibmcloud tke help` |
{: caption="Table 1. Describes the TKE CLI plug-in commands" caption-side="top"}

For more information on each command, run the following command in the TKE CLI plug-in:

```
ibmcloud tke help <command_name>
```
{: pre}
