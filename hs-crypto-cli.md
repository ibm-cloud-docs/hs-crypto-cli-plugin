---

copyright:
  years: 2018, 2021
lastupdated: "2021-08-25"

keywords: hpcs cli, hyper protect crypto services cli, Trusted Key Entry plug-in, cloud tke, TKE plug-in, CLI plug-in, TKE commands, Cloud TKE reference, cert manager cli plug-in, key management cli

subcollection: hs-crypto-cli-plugin

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} CLI
{: #hpcs-cli-plugin}

{{site.data.keyword.hscrypto}} provides multiple {{site.data.keyword.cloud}} CLI plug-ins for you to perform actions toward your service instances: key management CLI plug-in, Trusted Key Entry (TKE) CLI plug-in, and certificate manager CLI plug-in.
{:shortdesc}

## {{site.data.keyword.hscrypto}} key management CLI plug-in
{: #kp-cli-plugin}

{{site.data.keyword.hscrypto}} integrates with the {{site.data.keyword.keymanagementserviceshort}} CLI plug-in so that you can use the {{site.data.keyword.keymanagementserviceshort}} CLI plug-in to manage root keys and standard keys in your {{site.data.keyword.hscrypto}} instances.

- For how to set up the {{site.data.keyword.keymanagementserviceshort}} CLI plug-in for {{site.data.keyword.hscrypto}}, see [Performing key management operations with the CLI](/docs/hs-crypto?topic=hs-crypto-set-up-cli).
- For the complete key management CLI reference, see [{{site.data.keyword.keymanagementserviceshort}} CLI command reference](/docs/key-protect?topic=key-protect-cli-plugin-key-protect-cli-reference).

## {{site.data.keyword.hscrypto}} Trusted Key Entry CLI plug-in
{: #tke-cli-plugin}

You can use the TKE CLI plug-in to manage crypto units that are assigned to your account.

### Installing the TKE CLI plug-in
{: #install-tke-cli-plugin}

To install the TKE CLI plug-in, follow these steps:

1. Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started){: external}.

    {{site.data.keyword.cloud_notm}} CLI requires Java&trade; 1.8.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`.

2. Install the latest TKE plug-in with the following command:

    ```
    ibmcloud plugin install tke
    ```
    {: pre}

    You are notified on the command line when updates to the {{site.data.keyword.cloud_notm}} CLI and plug-ins are available. Be sure to keep your CLI up to date so that you can use the latest commands. You can view the current version of all installed plug-ins by running `ibmcloud plugin list`.
    {: tip}

3. Set the environment variable `CLOUDTKEFILES` on your workstation. Specify a directory where you want master key part files and signature key part files to be created and saved. Create the directory if it does not exist.

    - On the Linux&trade; operating system or MacOS, add the following line to the `.bash_profile` file:

        ```
        export CLOUDTKEFILES=<path>
        ```
        {: pre}

        For example, you can specify the *path* to `/Users/tke-files`.

    - On the Windows&trade; operating system, in **Control Panel**, type `environment variable` in the search box to locate the Environment Variables window. Create a CLOUDTKEFILES environment variable and set the value to the path to the key files. For example, `C:\users\tke-files`.

### TKE CLI plug-in commands
{: #tke-commands-usage}

| Command name | Description | Example |
| ------------ | ----------- | ------- |
| `tke auto-init` | Automatically initializes the service instance. | `ibmcloud tke auto-init` |
| `tke auto-mk-rotate` | Automatically rotates the master key with a randomly generated master key value in the recovery HSM. | `ibmcloud tke auto-mk-rotate` |
| `tke auto-recover` | Automatically copies the current master key value from the recovery HSM to other crypto units in the same resource group. | `tke auto-recover` |
| `tke` | Manages crypto units in the IBM Cloud. | `ibmcloud tke` |
| `tke cryptounit-add` | Adds crypto units to the set of crypto units to work with. | `ibmcloud tke cryptounit-add` |
| `tke cryptounit-admin-add` | Adds a crypto unit administrator to the selected crypto units. | `ibmcloud tke cryptounit-admin-add` |
| `tke cryptounit-admin-rm` | Removes a crypto unit administrator from the selected crypto units. | `ibmcloud tke cryptounit-admin-rm` |
| `tke cryptounit-admins` | Lists administrators installed in the selected crypto units. | `ibmcloud tke cryptounit-admins` |
| `tke cryptounit-compare` | Compares configuration settings of the selected crypto units. | `ibmcloud tke cryptounit-compare` |
| `tke cryptounit-cp-btc`|Enables bitcoin (BTC) related functions in the selected crypto units.|`ibmcloud tke cryptounit-cp-btc`|
| `tke cryptounit-cp-eddsa`|Enables Edwards-curve digital signature algorithms (EdDSA) functions in the selected crypto units.|`ibmcloud tke cryptounit-cp-eddsa`|
| `tke cryptounit-cp-sig-other`| Enables non-Elliptic-curve DSA, non-Edwards-curve DSA digital signature functions in the selected crypto units.|`ibmcloud tke cryptounit-cp-sig-other`|
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
| `tke failover-enable`   | Enable or add failover crypto units after you provision a service instance.  | `ibmcloud tke failover-enable`  |
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

## {{site.data.keyword.hscrypto}} certificate manager CLI plug-in
{: #cert-manager-cli-plugin}

You can use the certificate manager CLI plug-in to manage certificates and administrator signature keys for [the second layer of authentication in GREP11 or PKCS #11 API connections](/docs/hs-crypto?topic=hs-crypto-enable-authentication-ep11).

### Installing the certificate manager CLI plug-in
{: #install-cert-manager-cli-plugin}

To install the certificate manager CLI plug-in, follow these steps:

1. Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started){: external}.

    {{site.data.keyword.cloud_notm}} CLI requires Java&trade; 1.8.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`.

2. Install the latest certificate manager plug-in with the following command:

    ```
    ibmcloud plugin install hpcs-cert-mgr
    ```
    {: pre}

    You're notified on the command line when updates to the {{site.data.keyword.cloud_notm}} CLI and plug-ins are available. Be sure to keep your CLI up to date so that you can use the latest commands. You can view the current version of all installed plug-ins by running `ibmcloud plugin list`.
    {: tip}

### Certificate manager CLI plug-in commands
{: #cert-manager-commands-usage}

The following lists all the available certificate manager CLI commands and their corresponding usage. Use `-h` or `--help` for help information.

#### hpcs-cert-mgr adminkey get
{: #command-cert-manager-get-admin-key}

Use this command to retrieve the administrator signature key of the certificate administrator.

```
ibmcloud hpcs-cert-mgr adminkey get --crn HPCS_CRN [--private]
```

- Command options

    --crn HPCS_CRN
    :   Required. The `crn` of your {{site.data.keyword.hscrypto}} instance. You can use the `ibmcloud resource service-instances --long` command to retrieve the `crn`.

    --private
    :   Optional. If you use this option, the certificate manager server URL points to the private network. For example,: `cert-mgr.private.<region>.hs-crypto.cloud.ibm.com:443`. The `region` is the abbreviation of the geographic area where you log in to {{site.data.keyword.cloud_notm}}. In this case, you need to use the private network to connect your service instance.

- Example

  ```
  export HPCS_CRN=crn:v1:staging:public:xxx:yyy:zzz
  ```
  {: pre}

  ```
  ibmcloud hpcs-cert-mgr adminkey get --crn ${HPCS_CRN}
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  connecting to server [cert-mgr.us-south.hs-crypto.cloud.ibm.com:443]...
  +------------+--------+
  | PROPERTIES | VALUES |
  +------------+--------+
  | PublicKey  |        |
  +------------+--------+

  command completed successfully.
  ```
  {: screen}

#### hpcs-cert-mgr adminkey set
{: #command-cert-manager-set-admin-key}

Use this command to create the administrator signature key for the certificate administrator to connect to the certificate manager server.

```
ibmcloud hpcs-cert-mgr adminkey set --crn HPCS_CRN [--private]
```

- Command options

    --crn HPCS_CRN
    :   Required. The `crn` of your {{site.data.keyword.hscrypto}} instance. You can use the `ibmcloud resource service-instances --long` command to retrieve the `crn`.

    --private
    :   Optional. If you use this option, the certificate manager server URL points to the private network. For example,: `cert-mgr.private.<region>.hs-crypto.cloud.ibm.com:443`. The `region` is the abbreviation of the geographic area where you log in to {{site.data.keyword.cloud_notm}}. In this case, you need to use the private network to connect your service instance.

- Example

  ```
  export HPCS_CRN=crn:v1:staging:public:xxx:yyy:zzz
  ```
  {: pre}

  ```
  ibmcloud hpcs-cert-mgr adminkey set --crn ${HPCS_CRN}
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  connecting to server [cert-mgr.us-south.hs-crypto.cloud.ibm.com:443]...
  +------------+-----------------------------------------------------------------------------------+
  | KEYTYPE    | FILE                                                                              |
  +------------+-----------------------------------------------------------------------------------+
  | PrivateKey | /Users/username/.hpcs-cert-mgr-cfg/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX.priv  |
  | PublicKey  | /Users/username/.hpcs-cert-mgr-cfg/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX.pub   |
  +------------+-----------------------------------------------------------------------------------+

  An automatically generated keypair is stored locally and configured to node remotely, please keep the keypair carefully!!!

  command completed successfully.
  ```
  {: screen}

#### hpcs-cert-mgr adminkey update
{: #command-cert-manager-update-admin-key}

Use this command to refresh and update the administrator signature key for the certificate administrator.

```
ibmcloud hpcs-cert-mgr adminkey update --crn HPCS_CRN --admin-priv-key ADMIN_PRIV_KEY [--private]
```

- Command options

    --crn HPCS_CRN
    :   Required. The `crn` of your {{site.data.keyword.hscrypto}} instance. You can use the `ibmcloud resource service-instances --long` command to retrieve the `crn`.

    --admin-priv-key ADMIN_PRIV_KEY
    :   Required. The file path of the existing private key that is stored on your local workstation. The private key is used to sign this command action toward your instance certificate manager server.

    --private
    :   Optional. If you use this option, the certificate manager server URL points to the private network. For example,: `cert-mgr.private.<region>.hs-crypto.cloud.ibm.com:443`. The `region` is the abbreviation of the geographic area where you log in to {{site.data.keyword.cloud_notm}}. In this case, you need to use the private network to connect your service instance.

- Example

  ```
  export HPCS_CRN=crn:v1:staging:public:xxx:yyy:zzz
  ```
  {: pre}

  ```
  export ADMIN_PRIV_KEY=/Users/admin1/.hpcs-cert-mgr-cfg/44de77d2-599b-0089-2f0f-bad8d1c94a7c.priv
  ```
  {: pre}

  ```
  ibmcloud hpcs-cert-mgr adminkey update --crn ${HPCS_CRN} --admin-priv-key ${ADMIN_PRIV_KEY}
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  connecting to server [cert-mgr.us-south.hs-crypto.cloud.ibm.com:443]...
  +------------+-----------------------------------------------------------------------------------+
  | KEYTYPE    | FILE                                                                              |
  +------------+-----------------------------------------------------------------------------------+
  | PrivateKey | /Users/username/.hpcs-cert-mgr-cfg/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX.priv  |
  | PublicKey  | /Users/username/.hpcs-cert-mgr-cfg/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX.pub   |
  +------------+-----------------------------------------------------------------------------------+

  An automatically generated keypair is stored locally and configured to node remotely, please keep the keypair carefully!!!

  command completed successfully.
  ```
  {: screen}

#### hpcs-cert-mgr adminkey delete
{: #command-cert-manager-delete-admin-key}

Use this command to delete the administrator signature key for the certificate administrator.

```
ibmcloud hpcs-cert-mgr adminkey delete --crn HPCS_CRN --admin-priv-key ADMIN_PRIV_KEY [--private]
```

- Command options

    --crn HPCS_CRN
    :   Required. The `crn` of your {{site.data.keyword.hscrypto}} instance. You can use the `ibmcloud resource service-instances --long` command to retrieve the `crn`.

    --admin-priv-key ADMIN_PRIV_KEY
    :   Required. The file path of your current private key that is stored on your local workstation. The private key is used to sign this command action toward your instance certificate manager server.

    --private
    :   Optional. If you use this option, the certificate manager server URL points to the private network. For example,: `cert-mgr.private.<region>.hs-crypto.cloud.ibm.com:443`. The `region` is the abbreviation of the geographic area where you log in to {{site.data.keyword.cloud_notm}}. In this case, you need to use the private network to connect your service instance.

- Example

  ```
  export HPCS_CRN=crn:v1:staging:public:xxx:yyy:zzz
  ```
  {: pre}

  ```
  export ADMIN_PRIV_KEY=/Users/admin1/.hpcs-cert-mgr-cfg/44de77d2-599b-0089-2f0f-bad8d1c94a7c.priv
  ```
  {: pre}

  ```
  ibmcloud hpcs-cert-mgr adminkey delete --crn ${HPCS_CRN} --admin-priv-key ${ADMIN_PRIV_KEY}
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  connecting to server [cert-mgr.us-south.hs-crypto.cloud.ibm.com:443]...
  command completed successfully.
  ```
  {: screen}

#### hpcs-cert-mgr cert get
{: #command-cert-manager-get-cert}

Use this command to retrieve the client certificate on your instance certificate manager server.

```
ibmcloud hpcs-cert-mgr cert get --crn HPCS_CRN --cert-id CERT_ID [--cert-store-file CERT_FILE] [--private]
```

- Command options

    --crn HPCS_CRN
    :   Required. The `crn` of your {{site.data.keyword.hscrypto}} instance. You can use the `ibmcloud resource service-instances --long` command to retrieve the `crn`.

    --cert-id CERT_ID
    :   Required. The string ID of the client certificate that you want to retrieve.

    --cert-store-file CERT_FILE
    :   Optional. The file path to store the retrieved certificate. If you specify this option, the file is created on your local workstation and stores the certificate content.

    --private
    :   Optional. If you use this option, the certificate manager server URL points to the private network. For example,: `cert-mgr.private.<region>.hs-crypto.cloud.ibm.com:443`. The `region` is the abbreviation of the geographic area where you log in to {{site.data.keyword.cloud_notm}}. In this case, you need to use the private network to connect your service instance.

- Example

  ```
  export HPCS_CRN=crn:v1:staging:public:xxx:yyy:zzz
  ```
  {: pre}

  ```
  ibmcloud hpcs-cert-mgr cert get --crn ${HPCS_CRN} --cert-id testcert --cert-store-file c/b/cert.pem
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  connecting to server [cert-mgr.us-south.hs-crypto.cloud.ibm.com:443]...
  ------------------ The returned certification ------------------
  -----BEGIN CERTIFICATE-----
  MIIFazCCA10gAwIBAgIUVW/gPwBtOKHEwCL.........
  ............................................
  ............................................
  ................................FkQF0tfc6cg=
  -----END CERTIFICATE-----

  command completed successfully.
  ```
  {: screen}

#### hpcs-cert-mgr cert set
{: #command-cert-manager-set-cert}

Use this command to set client certificates for your instance certificate manager server.

```
ibmcloud hpcs-cert-mgr cert set --crn HPCS_CRN --admin-priv-key ADMIN_PRIV_KEY --cert-id CERT_ID --cert CERT_FILE [--private]
```

- Command options

    --crn HPCS_CRN
    :   Required. The `crn` of your {{site.data.keyword.hscrypto}} instance. You can use the `ibmcloud resource service-instances --long` command to retrieve the `crn`.

    --admin-priv-key ADMIN_PRIV_KEY
    :   Required. The file path of your current private key that is stored on your local workstation. The private key is used to sign this command action toward your instance certificate manager server.

    --cert-id CERT_ID
    :   Required. The string ID that you want to assign to the certificate for easy identification.

    --cert CERT_FILE
    :   Required. The certificate file that is stored on your workstation. It is suggested to use the {{site.data.keyword.cloud_notm}} Certificate Manager to order and manage SSL/TLS certificates for your applications and services.

    --private
    :   Optional. If you use this option, the certificate manager server URL points to the private network. For example,: `cert-mgr.private.<region>.hs-crypto.cloud.ibm.com:443`. The `region` is the abbreviation of the geographic area where you log in to {{site.data.keyword.cloud_notm}}. In this case, you need to use the private network to connect your service instance.

- Example

  ```
  export HPCS_CRN=crn:v1:staging:public:xxx:yyy:zzz
  ```
  {: pre}

  ```
  export CERT=/Users/admin1/cert.pem
  ```
  {: pre}

  ```
  export ADMIN_PRIV_KEY=/Users/admin1/.hpcs-cert-mgr-cfg/44de77d2-599b-0089-2f0f-bad8d1c94a7c.priv
  ```
  {: pre}

  ```
  ibmcloud hpcs-cert-mgr cert set --crn ${HPCS_CRN} --admin-priv-key ${ADMIN_PRIV_KEY} --cert-id testcert --cert ${CERT}
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  connecting to server [cert-mgr.us-south.hs-crypto.cloud.ibm.com:443]...
  command completed successfully.
  ```
  {: screen}

#### hpcs-cert-mgr cert list
{: #command-cert-manager-list-cert}

Use this command to list all the certificates that are managed by the administrator for your instance certificate manager server.

```
ibmcloud hpcs-cert-mgr cert list --crn HPCS_CRN [--private]
```

- Command options

    --crn HPCS_CRN
    :   Required. The `crn` of your {{site.data.keyword.hscrypto}} instance. You can use the `ibmcloud resource service-instances --long` command to retrieve the `crn`.

    --private
    :   Optional. If you use this option, the certificate manager server URL points to the private network. For example,: `cert-mgr.private.<region>.hs-crypto.cloud.ibm.com:443`. The `region` is the abbreviation of the geographic area where you log in to {{site.data.keyword.cloud_notm}}. In this case, you need to use the private network to connect your service instance.

- Example

  ```
  export HPCS_CRN=crn:v1:staging:public:xxx:yyy:zzz
  ```
  {: pre}

  ```
  ibmcloud hpcs-cert-mgr cert list --crn ${HPCS_CRN}
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  connecting to server [cert-mgr.us-south.hs-crypto.cloud.ibm.com:443]...
  +------------+----------------------------------------+
  | CERTID     | CERT                                   |
  | testcert   | -----BEGIN CERTIFICATE-----            |
  |            | MIIFazCCA10gAwIBAgIUVW/gPwBtOKHEwCL....|
  |            |........................................|
  |            |............................FkQF0tfc6cg=|
  |            | -----END CERTIFICATE-----              |
  |            |                                        |
  | testcert2  | -----BEGIN CERTIFICATE-----            |
  |            | MIIFazCCA10gAwIBAgIUVW/gPwBtOKHEwCL....|
  |            |........................................|
  |            |............................FkQF0tfc6cg=|
  |            | -----END CERTIFICATE-----              |
  |            |                                        |
  +------------+----------------------------------------+

  command completed successfully.
  ```
  {: screen}

#### hpcs-cert-mgr cert delete
{: #command-cert-manager-delete-cert}

Use this command to delete client certificates for your instance certificate manager server.

```
ibmcloud hpcs-cert-mgr cert delete --crn HPCS_CRN --admin-priv-key ADMIN_PRIV_KEY --cert-id CERT_ID [--private]
```

- Command options

    --crn HPCS_CRN
    :   Required. The `crn` of your {{site.data.keyword.hscrypto}} instance. You can use the `ibmcloud resource service-instances --long` command to retrieve the `crn`.

    --admin-priv-key ADMIN_PRIV_KEY
    :   Required. The file path of your current private key that is stored on your local workstation. The private key is used to sign this command action toward your instance certificate manager server.

    --cert-id CERT_ID
    :   Required. The string ID of the certificate that you want to delete.

    --private
    :   Optional. If you use this option, the certificate manager server URL points to the private network. For example,: `cert-mgr.private.<region>.hs-crypto.cloud.ibm.com:443`. The `region` is the abbreviation of the geographic area where you log in to {{site.data.keyword.cloud_notm}}. In this case, you need to use the private network to connect your service instance.

- Example

  ```
  export HPCS_CRN=crn:v1:staging:public:xxx:yyy:zzz
  ```
  {: pre}

  ```
  export ADMIN_PRIV_KEY=/Users/admin1/.hpcs-cert-mgr-cfg/44de77d2-599b-0089-2f0f-bad8d1c94a7c.priv
  ```
  {: pre}

  ```
  ibmcloud hpcs-cert-mgr cert delete --crn ${HPCS_CRN} --admin-priv-key ${ADMIN_PRIV_KEY} --cert-id testcert
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  connecting to server [cert-mgr.us-south.hs-crypto.cloud.ibm.com:443]...
  command completed successfully.
  ```
  {: screen}
