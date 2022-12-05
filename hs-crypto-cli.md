---

copyright:
  years: 2018, 2022
lastupdated: "2022-05-30"

keywords: hpcs cli, hyper protect crypto services cli, trusted key entry plug-in, cloud tke, tke plug-in, cli plug-in, tke commands, cloud tke reference, cert manager cli plug-in, key management cli, uko cli, united key orchestrator cli

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

{{site.data.keyword.hscrypto}} provides multiple {{site.data.keyword.cloud}} CLI plug-ins for you to perform actions toward your service instances: key management CLI plug-in, Trusted Key Entry (TKE) CLI plug-in, certificate manager CLI plug-in, and {{site.data.keyword.uko_full_notm}} (UKO) CLI plug-in.
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
| `tke auto-recover` | Automatically copies the current master key value from the recovery HSM to other crypto units in the same resource group. | `ibmcloud tke auto-recover` |
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

## {{site.data.keyword.hscrypto}} {{site.data.keyword.uko_full_notm}} CLI plug-in
{: #uko-cli-plugin}

You can use the {{site.data.keyword.uko_full_notm}} CLI plug-in to manage vaults, keystores, and managed keys for {{site.data.keyword.hscrypto}} instances with the {{site.data.keyword.uko_full_notm}} plan.

### Installing the {{site.data.keyword.uko_full_notm}} CLI plug-in
{: #install-uko-cli-plugin}

To install the {{site.data.keyword.uko_full_notm}} CLI plug-in, follow these steps:

1. Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started){: external}.

    {{site.data.keyword.cloud_notm}} CLI requires Java&trade; 1.8.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`.

2. Install the latest {{site.data.keyword.uko_full_notm}} CLI plug-in with the following command:

    ```
    ibmcloud plugin install hpcs
    ```
    {: pre}

    You're notified on the command line when updates to the {{site.data.keyword.cloud_notm}} CLI and plug-ins are available. Be sure to keep your CLI up to date so that you can use the latest commands. You can view the current version of all installed plug-ins by running `ibmcloud plugin list`.
    {: tip}

3. Set the environment variable `UKO_URL` on your workstation.

    ```
    export UKO_URL=<UKO_endpoint_URL>
    ```
    {: pre}

    Replace `<UKO_endpoint_URL>` with your instance UKO endpoint URL. You can get the endpoint URL on your provisioned service instance UI dashboard through **Overview** &gt; **Connect** &gt; **{{site.data.keyword.uko_full_notm}} endpoint URL**. Or, you can dynamically [retrieve the API endpoint URL](/apidocs/uko#endpoint-urls){: external}. 

### {{site.data.keyword.uko_full_notm}} CLI plug-in commands
{: #uko-commands-usage}

The following lists all the available {{site.data.keyword.uko_full_notm}} CLI commands and their corresponding usage. Use `-h` or `--help` for help information.

#### hpcs uko managed-keys
{: #command-uko-list-managed-keys}

Use this command to list managed keys in the instance.

```
ibmcloud hpcs uko managed-keys [--vault-id VAULT_ID] [--algorithm ALGORITHM] [--state STATE] [--limit LIMIT] [--offset OFFSET]
```

- Command options

    --vault-id (string)
    :   Optional. The Universally Unique Identifier (UUID) of the vault. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the UUID. The length must be 36 characters. The value must match the regular expression `/^[-0-9a-z]+$/`.

    --algorithm (string)
    :   Optional. The algorithm of returned keys. Values that can be set are `aes` and `rsa`.

    --state (string)
    :   Optional. The state that returned keys are to be in. The default value is `active`. Values that can be set are: `pre_activation`, `active`, `deactivated`, and `destroyed`.

    --limit (int64)
    :   Optional. The number of keys to retrieve. The maximum value is `1000`. The minimum value is `1`.

    --offset (int64)
    :   Optional. The number of keys to skip. The minimum value is `0`.

- Example

  ```
  ibmcloud hpcs uko managed-keys --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  {
    "first": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys?vault.id=eb66ebbd-7230-4cde-89bf-17282cda5faa\u0026limit=20"
    },
    "last": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys?vault.id=eb66ebbd-7230-4cde-89bf-17282cda5faa\u0026limit=20\u0026offset=0"
    },
    "limit": null,
    "managed_keys": [
      {
        "activation_date": "2027-07-05",
        "algorithm": "aes",
        "created_at": "2022-05-26T14:18:09.000Z",
        "created_by": "IBMid-666000MBI9",
        "description": "new description",
        "expiration_date": "2028-09-16",
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
        "id": "21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
        "instances": [
          {
            "id": "fa0e9e55-742c-4680-89b5-cad3acf9d6d1",
            "keystore": {
              "group": "Production",
              "type": "ibm_cloud_kms"
            },
            "label_in_keystore": "IBM CLOUD KEY",
            "type": "secret_key"
          }
        ],
        "label": "IBM CLOUD KEY",
        "referenced_keystores": [],
        "size": "256",
        "state": "active",
        "tags": [
          {
            "name": "first-tag",
            "value": "for-IBM-CLOUD"
          }
        ],
        "template": {
          "id": "67a14437-3838-4fdf-b84d-1ed062585548",
          "name": "IBM-Cloud-Template"
        },
        "updated_at": "2022-05-26T14:18:10.000Z",
        "updated_by": "IBMid-666000MBI9",
        "vault": {
          "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
          "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
          "name": "Test_Vault_Go_Cli"
        },
        "verification_patterns": [
          {
            "method": "ENC-ZERO",
            "value": "0F5895"
          }
        ]
      }
    ],
    "offset": null,
    "total_count": 1
  }
  ```
  {: screen}

#### hpcs uko managed-key-create
{: #command-uko-create-managed-key}

Use this command to create a new key based on the supplied template. The template must exist in your instance before you can run this command.

```
ibmcloud hpcs uko managed-key-create --uko-vault UKO_VAULT --template-name TEMPLATE_NAME --vault VAULT --label LABEL [--tags TAGS] [--description DESCRIPTION] 
```

- Command options

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the UUID.

    --template-name (string)
    :   Required. The name of the key template to use when you create a key. The length must be between 1 to 30 characters. The value must match the regular expression `/^[A-Za-z][A-Za-z0-9-]+$/`.

    --vault ([VaultReferenceInCreationRequest](#uko-vault-reference-in-creation-request-example-schema))
    :   Required. The ID of the vault where the managed key is to be created.

    --label (string)
    :   Required. The label of the key. The length must be between 1 to 30 characters. The value must match the regular expression `/^[A-Za-z0-9._ -]+$/`.

    --tags ([Tag\[\]](#uko-tag-example-schema))
    :   Optional. Key-value pairs that are associated with the key. The maximum length is `128` items. The minimum length is `0` items.

    --description (string)
    :   Optional. The description of the managed key. The length must be between 0 to 200 characters. The value must match the regular expression `/(.|\\n)*/`.

- Example

  ```
  ibmcloud hpcs uko managed-key-create \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --template-name=IBM-Cloud-Template \
    --vault='{"id": "eb66ebbd-7230-4cde-89bf-17282cda5faa"}' \
    --label='IBM CLOUD KEY' \
    --tags='[{"name": "first-tag", "value": "for-IBM-CLOUD"}]' \
    --description="new description" \
    --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-26T14:18:10Z
  {
    "activation_date": "2027-07-05",
    "algorithm": "aes",
    "created_at": "2022-05-26T14:18:09.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "new description",
    "expiration_date": "2028-09-16",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "id": "21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "instances": [
      {
        "id": "fa0e9e55-742c-4680-89b5-cad3acf9d6d1",
        "keystore": {
          "group": "Production",
          "type": "ibm_cloud_kms"
        },
        "label_in_keystore": "IBM CLOUD KEY",
        "type": "secret_key"
      }
    ],
    "label": "IBM CLOUD KEY",
    "referenced_keystores": [],
    "size": "256",
    "state": "active",
    "tags": [
      {
        "name": "first-tag",
        "value": "for-IBM-CLOUD"
      }
    ],
    "template": {
      "id": "67a14437-3838-4fdf-b84d-1ed062585548",
      "name": "IBM-Cloud-Template"
    },
    "updated_at": "2022-05-26T14:18:10.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "name": "Test_Vault_Go_Cli"
    },
    "verification_patterns": [
      {
        "method": "ENC-ZERO",
        "value": "0F5895"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko managed-key-delete
{: #command-uko-delete-managed-key}

Use this command to delete a managed key by key ID from the vault. Make sure that the key is in a `destroyed` state before you run this command.

```
ibmcloud hpcs uko managed-key-delete --id ID --uko-vault UKO_VAULT --if-match IF_MATCH 
```

- Command options

    --id (string)
    :   Required. The UUID of the key. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the key UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the vault UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko managed-key` command to retrieve the ETag.

- Example

  ```
  ibmcloud hpcs uko managed-key-delete \
    --id=21a7498e-2ae4-47ee-85ac-a19bf64e92fa \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --if-match=2022-05-27T10:15:38Z
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ...
  OK
  ```
  {: screen}

#### hpcs uko managed-key
{: #command-uko-retrieve-a-key}

Use this command to retrieve a managed key and its details by specifying the key ID.

```
ibmcloud hpcs uko managed-key --id ID --uko-vault UKO_VAULT 
```

- Command options

    --id (string)
    :   Required. The UUID of the key. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the key UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the vault UUID.

- Example

  ```
  ibmcloud hpcs uko managed-key \
    --id=21a7498e-2ae4-47ee-85ac-a19bf64e92fa \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-26T14:18:10Z
  {
    "activation_date": "2027-07-05",
    "algorithm": "aes",
    "created_at": "2022-05-26T14:18:09.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "new description",
    "expiration_date": "2028-09-16",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "id": "21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "instances": [
      {
        "id": "fa0e9e55-742c-4680-89b5-cad3acf9d6d1",
        "keystore": {
          "group": "Production",
          "type": "ibm_cloud_kms"
        },
        "label_in_keystore": "IBM CLOUD KEY",
        "type": "secret_key"
      }
    ],
    "label": "IBM CLOUD KEY",
    "referenced_keystores": [],
    "size": "256",
    "state": "active",
    "tags": [
      {
        "name": "first-tag",
        "value": "for-IBM-CLOUD"
      }
    ],
    "template": {
      "id": "67a14437-3838-4fdf-b84d-1ed062585548",
      "name": "IBM-Cloud-Template"
    },
    "updated_at": "2022-05-26T14:18:10.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "name": "Test_Vault_Go_Cli"
    },
    "verification_patterns": [
      {
        "method": "ENC-ZERO",
        "value": "0F5895"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko managed-key-update
{: #command-uko-managed-key-update}

Use this command to update attributes of a managed key. You can only modify the key's state separately from other changes. Changing a key's state affects its availability for cryptographic operations in keystores.

```
ibmcloud hpcs uko managed-key-update --id ID --uko-vault UKO_VAULT --if-match IF_MATCH [--label LABEL] [--activation-date ACTIVATION_DATE] [--expiration-date EXPIRATION_DATE] [--tags TAGS] [--description DESCRIPTION] 
```

- Command options

    --id (string)
    :   Required. The UUID of the key. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the key UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the vault UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko managed-key` command to retrieve the ETag.

    --label (string)
    :   Required. The label of the key. The length must be between 1 to 30 characters. The value must match the regular expression `/^[A-Za-z0-9._ -]+$/`.

    --activation-date (strfmt.Date)
    :   Optional. The activation date must be provided in format YYYY-MM-DD.

    --expiration-date (strfmt.Date)
    :   Optional. The expiration date must be provided in format YYYY-MM-DD.

    --tags ([Tag\[\]](#uko-tag-example-schema))
    :   Optional. Key-value pairs that are associated with the key. The maximum length is `128` items. The minimum length is `0` items.

    --description (string)
    :   Optional. The description of the managed key. The length must be between 0 to 200 characters. The value must match the regular expression `/(.|\\n)*/`.

- Example

  ```
  ibmcloud hpcs uko managed-key-update \
    --id=21a7498e-2ae4-47ee-85ac-a19bf64e92fa \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --if-match=2022-05-26T14:18:10Z \
    --description="updated description" \
    --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:
  
  ```
  ETag
  2022-05-26T14:26:39Z
  {
    "activation_date": "2027-07-05",
    "algorithm": "aes",
    "created_at": "2022-05-26T14:18:09.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "updated description",
    "expiration_date": "2028-09-16",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "id": "21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "instances": [
      {
        "id": "fa0e9e55-742c-4680-89b5-cad3acf9d6d1",
        "keystore": {
          "group": "Production",
          "type": "ibm_cloud_kms"
        },
        "label_in_keystore": "IBM CLOUD KEY",
        "type": "secret_key"
      }
    ],
    "label": "IBM CLOUD KEY",
    "referenced_keystores": [],
    "size": "256",
    "state": "active",
    "tags": [
      {
        "name": "first-tag",
        "value": "for-IBM-CLOUD"
      }
    ],
    "template": {
      "id": "67a14437-3838-4fdf-b84d-1ed062585548",
      "name": "IBM-Cloud-Template"
    },
    "updated_at": "2022-05-26T14:26:39.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "name": "Test_Vault_Go_Cli"
    },
    "verification_patterns": [
      {
        "method": "ENC-ZERO",
        "value": "0F5895"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko managed-key-ds
{: #command-uko-key-distribution}

Use this command to return the keystore distribution status for a managed key. If there are any problems reading the keystore status, http code `200` will still be returned, and the error code will be returned alongside an 'error' keystore status.

```
ibmcloud hpcs uko managed-key-ds --id ID --uko-vault UKO_VAULT
```

- Command options

    --id (string)
    :   Required. The UUID of the key. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the key UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the vault UUID.

- Example

  ```
  ibmcloud hpcs uko managed-key-ds \
    --id=21a7498e-2ae4-47ee-85ac-a19bf64e92fa \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  {
    "status_in_keystores": [
      {
        "keystore": {
          "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/10921d25-174e-4229-ae36-d9f02b816ce5",
          "id": "10921d25-174e-4229-ae36-d9f02b816ce5",
          "name": "AWS KMS Keystore Name",
          "type": "aws_kms"
        },
        "status": "not_present"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko managed-key-update-from-template
{: #command-uko-managed-key-update-from-template}

Use this command to update a managed key to match the latest version of the associated key template. You can install, activate, or deactivate the key on target keystores in the group defined by the key template.

```
ibmcloud hpcs uko managed-key-update-from-template --id ID --uko-vault UKO_VAULT --if-match IF_MATCH 
```

- Command options

    --id (string)
    :   Required. The UUID of the key. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the key UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the vault UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko managed-key` command to retrieve the ETag.

- Example

  ```
  ibmcloud hpcs uko managed-key-update-from-template \
    --id=22c04c00-0687-4f10-b0ac-b9f01d68ee85 \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --output json --if-match=2022-05-27T12:27:37Z
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-27T12:29:46Z
  {
    "activation_date": "2027-07-06",
    "algorithm": "aes",
    "created_at": "2022-05-27T12:25:34.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "new description",
    "expiration_date": "2028-09-17",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/22c04c00-0687-4f10-b0ac-b9f01d68ee85",
    "id": "22c04c00-0687-4f10-b0ac-b9f01d68ee85",
    "instances": [
      {
        "id": "7adbf773-ebbe-445e-816b-3838cde11430",
        "keystore": {
          "group": "Production",
          "type": "ibm_cloud_kms"
        },
        "label_in_keystore": "IBM CLOUD KEY2",
        "type": "secret_key"
      }
    ],
    "label": "IBM CLOUD KEY2",
    "referenced_keystores": [
      {
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/f779c44d-b90e-4917-b8b0-28d4591fefda",
        "id": "f779c44d-b90e-4917-b8b0-28d4591fefda",
        "name": "AWS KMS Keystore Name",
        "type": "aws_kms"
      }
    ],
    "size": "256",
    "state": "active",
    "tags": [
      {
        "name": "first-tag",
        "value": "for-IBM-CLOUD"
      }
    ],
    "template": {
      "id": "67a14437-3838-4fdf-b84d-1ed062585548",
      "name": "IBM-Cloud-Template"
    },
    "updated_at": "2022-05-27T12:29:46.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "name": "Test_Vault_Go_Cli"
    },
    "verification_patterns": [
      {
        "method": "ENC-ZERO",
        "value": "0D2611"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko managed-key-activate
{: #command-uko-managed-key-activate}

Use this command to activate a managed key and perform key installation or activation operations on keystores in the keystore group associated with the managed key.

```
ibmcloud hpcs uko managed-key-activate --id ID --uko-vault UKO_VAULT --if-match IF_MATCH 
```

- Command options

    --id (string)
    :   Required. The UUID of the key. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the key UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the vault UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko managed-key` command to retrieve the ETag.

- Example

  ```
  ibmcloud hpcs uko managed-key-activate \
    --id=21a7498e-2ae4-47ee-85ac-a19bf64e92fa \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --if-match=2022-05-27T10:06:27Z \
    --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-27T10:11:06Z
  {
    "activation_date": "2027-07-05",
    "algorithm": "aes",
    "created_at": "2022-05-26T14:18:09.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "updated description",
    "expiration_date": "2028-09-16",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "id": "21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "instances": [
      {
        "id": "fa0e9e55-742c-4680-89b5-cad3acf9d6d1",
        "keystore": {
          "group": "Production",
          "type": "ibm_cloud_kms"
        },
        "label_in_keystore": "IBM CLOUD KEY",
        "type": "secret_key"
      }
    ],
    "label": "IBM CLOUD KEY",
    "referenced_keystores": [
      {
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/f779c44d-b90e-4917-b8b0-28d4591fefda",
        "id": "f779c44d-b90e-4917-b8b0-28d4591fefda",
        "name": "AWS KMS Keystore Name",
        "type": "aws_kms"
      }
    ],
    "size": "256",
    "state": "active",
    "tags": [
      {
        "name": "first-tag",
        "value": "for-IBM-CLOUD"
      }
    ],
    "template": {
      "id": "67a14437-3838-4fdf-b84d-1ed062585548",
      "name": "IBM-Cloud-Template"
    },
    "updated_at": "2022-05-27T10:11:06.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "name": "Test_Vault_Go_Cli"
    },
    "verification_patterns": [
      {
        "method": "ENC-ZERO",
        "value": "0F5895"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko managed-key-deactivate
{: #command-uko-managed-key-deactivate}

Use this command to deactivates a managed key and perform key deactivation operations on keystores in the keystore group associated with the managed key.

```
ibmcloud hpcs uko managed-key-deactivate --id ID --uko-vault UKO_VAULT --if-match IF_MATCH 
```

- Command options

    --id (string)
    :   Required. The UUID of the key. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the key UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the vault UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko managed-key` command to retrieve the ETag.

- Example

  ```
  ibmcloud hpcs uko managed-key-deactivate \
    --id=21a7498e-2ae4-47ee-85ac-a19bf64e92fa \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --if-match=2022-05-27T10:13:31Z \
    --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-27T10:14:13Z
  {
    "activation_date": "2027-07-05",
    "algorithm": "aes",
    "created_at": "2022-05-26T14:18:09.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "updated description",
    "expiration_date": "2028-09-16",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "id": "21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "instances": [
      {
        "id": "fa0e9e55-742c-4680-89b5-cad3acf9d6d1",
        "keystore": {
          "group": "Production",
          "type": "ibm_cloud_kms"
        },
        "label_in_keystore": "IBM CLOUD KEY",
        "type": "secret_key"
      }
    ],
    "label": "IBM CLOUD KEY",
    "referenced_keystores": [
      {
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/f779c44d-b90e-4917-b8b0-28d4591fefda",
        "id": "f779c44d-b90e-4917-b8b0-28d4591fefda",
        "name": "AWS KMS Keystore Name",
        "type": "aws_kms"
      }
    ],
    "size": "256",
    "state": "deactivated",
    "tags": [
      {
        "name": "first-tag",
        "value": "for-IBM-CLOUD"
      }
    ],
    "template": {
      "id": "67a14437-3838-4fdf-b84d-1ed062585548",
      "name": "IBM-Cloud-Template"
    },
    "updated_at": "2022-05-27T10:14:13.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "name": "Test_Vault_Go_Cli"
    },
    "verification_patterns": [
      {
        "method": "ENC-ZERO",
        "value": "0F5895"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko managed-key-destroy
{: #command-uko-managed-key-destroy}

Use this command to destroys a managed key and perform key destruction operations on keystores in the keystore group associated with the managed key. This operation cannot be undone. Make sure that the managed key is in a `deactivated` state before you run this command.

```
ibmcloud hpcs uko managed-key-destroy --id ID --uko-vault UKO_VAULT --if-match IF_MATCH 
```

- Command options

    --id (string)
    :   Required. The UUID of the key. You can use the `ibmcloud hpcs uko managed-keys` command to retrieve the key UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the vault UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko managed-key` command to retrieve the ETag.

- Example

  ```
  ibmcloud hpcs uko managed-key-destroy \
    --id=21a7498e-2ae4-47ee-85ac-a19bf64e92fa \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --if-match=2022-05-27T10:14:13Z \
    --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-27T10:15:38Z
  {
    "activation_date": "2027-07-05",
    "algorithm": "aes",
    "created_at": "2022-05-26T14:18:09.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "updated description",
    "expiration_date": "2028-09-16",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "id": "21a7498e-2ae4-47ee-85ac-a19bf64e92fa",
    "instances": [
      {
        "id": "fa0e9e55-742c-4680-89b5-cad3acf9d6d1",
        "keystore": {
          "group": "Production",
          "type": "ibm_cloud_kms"
        },
        "label_in_keystore": "IBM CLOUD KEY",
        "type": "secret_key"
      }
    ],
    "label": "IBM CLOUD KEY",
    "referenced_keystores": [
      {
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/f779c44d-b90e-4917-b8b0-28d4591fefda",
        "id": "f779c44d-b90e-4917-b8b0-28d4591fefda",
        "name": "AWS KMS Keystore Name",
        "type": "aws_kms"
      }
    ],
    "size": "256",
    "state": "destroyed",
    "tags": [
      {
        "name": "first-tag",
        "value": "for-IBM-CLOUD"
      }
    ],
    "template": {
      "id": "67a14437-3838-4fdf-b84d-1ed062585548",
      "name": "IBM-Cloud-Template"
    },
    "updated_at": "2022-05-27T10:15:38.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
      "name": "Test_Vault_Go_Cli"
    },
    "verification_patterns": [
      {
        "method": "ENC-ZERO",
        "value": "0F5895"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko key-templates
{: #command-uko-key-templates}

Use this command to list all key templates in the instance.

```
ibmcloud hpcs uko key-templates [--vault-id VAULT_ID] [--key-algorithm KEY_ALGORITHM] [--limit LIMIT] [--offset OFFSET]
```

- Command options

    --vault-id (string)
    :   Optional. The UUID of the vault. The length must be 36 characters. The value must match the regular expression `/^[-0-9a-z]+$/`.

    --algorithm (string)
    :   Optional. The algorithm of the returned key templates. Values that can be set are `aes` and `rsa`.

    --limit (int64)
    :   Optional. The number of key templates to retrieve. The maximum value is `1000`. The minimum value is `1`.

    --offset (int64)
    :   Optional. The number of keys to skip. The minimum value is `0`.

- Example

  ```
  ibmcloud hpcs uko key-templates --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  {
    "first": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/templates?vault.id=5d1b7665-3652-4bc8-a1ee-3ea820919613\u0026limit=20"
    },
    "last": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/templates?vault.id=5d1b7665-3652-4bc8-a1ee-3ea820919613\u0026limit=20\u0026offset=0"
    },
    "limit": null,
    "offset": null,
    "templates": [
      {
      "created_at": "2022-05-20T15:13:37.000Z",
      "created_by": "IBMid-666000MBI9",
      "description": "Example IBM Cloud key template description",
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/templates/ee1e753c-fd13-4faa-a026-71c195ab6899",
      "id": "ee1e753c-fd13-4faa-a026-71c195ab6899",
      "key": {
          "activation_date": "P5Y1M1W2D",
          "algorithm": "aes",
          "expiration_date": "P1Y2M1W4D",
          "size": "256",
          "state": "active"
      },
      "keystores": [
          {
          "group": "Production",
          "type": "ibm_cloud_kms"
          }
      ],
      "name": "IBM-Cloud-Template",
      "updated_at": "2022-05-20T15:13:37.000Z",
      "updated_by": "IBMid-666000MBI9",
      "vault": {
          "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
          "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
          "name": "Example Vault"
      },
      "version": 0
      },
        "version": 1
      }
    ],
    "total_count": 1
  }
  ```
  {: screen}

#### ibmcloud hpcs uko key-template-create
{: #command-uko-key-template-create}

Use this command to create a new key template. Key templates are used to combine information that is necessary for creating a key. With key templates, you can easily create subsequent keys without specifying any details.

```
ibmcloud hpcs uko key-template-create --uko-vault UKO_VAULT --vault VAULT --name NAME --key KEY --keystores KEYSTORES [--description DESCRIPTION] 
```

- Command options

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko key-templates` command to retrieve the UUID.

    --vault ([VaultReferenceInCreationRequest](#uko-vault-reference-in-creation-request-example-schema))
    :   Required. The ID of the vault where the key template is to be created.

    --name (string)
    :   Required. The name of the template. You need to reference it when creating managed keys. The length must be between 1 and 30 characters. The value must match the regular expression `/^[A-Za-z][A-Za-z0-9-]*$/`.

    --key ([KeyProperties](#uko-key-properties-example-schema))
    :   Required. Properties that describe the managed key.

    --keystores ([KeystoresProperties\[\]](#uko-keystores-properties-example-schema))
    :   Required. An array describing the type and group of target keystores that the managed key is to be installed in. The maximum length is `1` item. The minimum length is `1` item. 
    
    --description (string)
    :   Optional. The description of the key template. The length must be between 0 to 200 characters. The value must match the regular expression `/(.|\\n)*/`.

- Example

  ```
  ibmcloud hpcs uko key-template-create \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --vault='{"id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b"}' \
      --name=IBM-Cloud-Template \
      --key='{"size": "256", "algorithm": "aes", "activation_date": "P5Y1M1W2D", "expiration_date": "P1Y2M1W4D", "state": "active"}' \
      --keystores='[{"group": "Production", "type": "ibm_cloud_kms"}]' \
      --description="Example IBM Cloud key template description" \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T15:13:37Z
  {
    "created_at": "2022-05-20T15:13:37.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "Example IBM Cloud key template description",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/templates/ee1e753c-fd13-4faa-a026-71c195ab6899",
    "id": "ee1e753c-fd13-4faa-a026-71c195ab6899",
    "key": {
      "activation_date": "P5Y1M1W2D",
      "algorithm": "aes",
      "expiration_date": "P1Y2M1W4D",
      "size": "256",
      "state": "active"
    },
    "keystores": [
      {
        "group": "Production",
        "type": "ibm_cloud_kms"
      }
    ],
    "name": "IBM-Cloud-Template",
    "updated_at": "2022-05-20T15:13:37.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "name": "Example Vault"
    },
    "version": 0
  }
  ```
  {: screen}

#### hpcs uko key-template-delete
{: #command-uko-key-template-delete}

Use this command to delete a key template from the vault. Make sure that no managed key is associated with the key template before you run this command.

```
ibmcloud hpcs uko key-template-delete --id ID --uko-vault UKO_VAULT --if-match IF_MATCH 
```

- Command options

    --id (string)
    :   Required. The UUID of the template. You can use the `ibmcloud hpcs uko key-templates` command to retrieve the UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko key-templates` command to retrieve the UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko key-template` command to retrieve the ETag.

- Example

  ```
  ibmcloud hpcs uko key-template-delete \
      --id=07b62c12-75a2-46c9-9259-0cecde3985d2 \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --if-match=2022-05-11T14:58:26Z \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ...
  OK
  ```
  {: screen}

#### ibmcloud hpcs uko key-template
{: #command-uko-key-template}

Use this command to retrieve a key template and its details by specifying the ID.

```
ibmcloud hpcs uko key-template --id ID --uko-vault UKO_VAULT 
```

- Command options

    --id (string)
    :   Required. The UUID of the template. You can use the `ibmcloud hpcs uko key-templates` command to retrieve the UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko key-templates` command to retrieve the UUID.

- Example

  ```
  ibmcloud hpcs uko key-template \
      --id=07b62c12-75a2-46c9-9259-0cecde3985d2 \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T15:13:37Z
  {
    "created_at": "2022-05-20T15:13:37.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "Example IBM Cloud key template description",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/templates/ee1e753c-fd13-4faa-a026-71c195ab6899",
    "id": "ee1e753c-fd13-4faa-a026-71c195ab6899",
    "key": {
      "activation_date": "P5Y1M1W2D",
      "algorithm": "aes",
      "expiration_date": "P1Y2M1W4D",
      "size": "256",
      "state": "active"
    },
    "keystores": [
      {
        "group": "Production",
        "type": "ibm_cloud_kms"
      }
    ],
    "name": "IBM-Cloud-Template",
    "updated_at": "2022-05-20T15:13:37.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "name": "Example Vault"
    },
    "version": 0
  }
  ```
  {: screen}

#### hpcs uko key-template-update
{: #command-uko-key-template-update}

Use this command to update attributes of a key template.

```
ibmcloud hpcs uko key-template-update --id ID --uko-vault UKO_VAULT --if-match IF_MATCH [--keystores KEYSTORES] [--description DESCRIPTION] [--key KEY] 
```

- Command options

    --id (string)
    :   Required. The UUID of the template. You can use the `ibmcloud hpcs uko key-templates` command to retrieve the UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko key-templates` command to retrieve the UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko key-template` command to retrieve the ETag.

    --keystores ([KeystoresPropertiesUpdate\[\]](#uko-keystores-properties-update-example-schema))
    :   Optional. An array describing the type and group of target keystores where the managed key is to be installed. The maximum length is `1` item. The minimum length is `1` item.
    
    --description (string)
    :   Optional. The updated description of the key template. The length must be between 0 to 200 characters. The value must match the regular expression `/(.|\\n)*/`.

    --key ([KeyPropertiesUpdate](#uko-key-properties-update-example-schema))
    :   Optional. Properties of the managed key.

- Example

  ```
  ibmcloud hpcs uko key-template-update \
      --id=07b62c12-75a2-46c9-9259-0cecde3985d2 \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --if-match=2022-05-11T14:58:26Z \
      --description="updated description" \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T15:20:06Z
  {
    "created_at": "2022-05-20T15:13:37.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "updated description",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/templates/07b62c12-75a2-46c9-9259-0cecde3985d2",
    "id": "07b62c12-75a2-46c9-9259-0cecde3985d2",
    "key": {
      "activation_date": "P5Y1M1W2D",
      "algorithm": "aes",
      "expiration_date": "P1Y2M1W4D",
      "size": "256",
      "state": "active"
    },
    "keystores": [
      {
        "group": "Production",
        "type": "ibm_cloud_kms"
      }
    ],
    "name": "IBM-Cloud-Template",
    "updated_at": "2022-05-20T15:20:06.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "name": "Example Vault"
    },
    "version": 1
  }
  ```
  {: screen}

#### hpcs uko keystores
{: #command-uko-list-keystores}

Use this command to list all target keystores in the instance.

```
ibmcloud hpcs uko keystores [--type TYPE] [--group GROUP] [--vault-id VAULT_ID] [--limit LIMIT] [--offset OFFSET]
```

- Command options

    --type (string)
    :   Optional. The type of keystores that you want to retrieve. Values that can be set are: `aws_kms`, `azure_key_vault`, and `ibm_cloud_kms`.

    --group (string)
    :   Optional. The keystore group.

    --vault-id (string)
    :   Optional. The UUID of the vault. The length must be 36 characters. The value must match the regular expression `/^[-0-9a-z]+$/`.

    --limit (int64)
    :   Optional. The number of keystores to retrieve. The maximum value is `1000`. The minimum value is `1`.

    --offset (int64)
    :   Optional. The number of keys to skip. The minimum value is `0`.

- Example

  ```
  ibmcloud hpcs uko keystores --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  {
    "first": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores?vault.id=5295ad47-2ce9-43c3-b9e7-e5a9482c362b\u0026limit=20"
    },
    "keystores": [
      {
        "aws_access_key_id": "",
        "aws_region": "eu_central_1",
        "aws_secret_access_key": "",
        "created_at": "2022-05-20T10:45:19.000Z",
        "created_by": "IBMid-666000MBI9",
        "description": "AWS KMS keystore",
        "groups": [
          "Production-UK",
          "Production-DE"
        ],
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/c90c69fa-50bf-4eaf-b972-63c97804c35d",
        "id": "c90c69fa-50bf-4eaf-b972-63c97804c35d",
        "location": "eu_central_1",
        "name": "AWS KMS Keystore Name",
        "type": "aws_kms",
        "updated_at": "2022-05-20T10:45:19.000Z",
        "updated_by": "IBMid-666000MBI9",
        "vault": {
          "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
          "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
          "name": "Example Vault"
        }
      },
      {
        "aws_access_key_id": "",
        "aws_region": "eu_central_1",
        "aws_secret_access_key": "",
        "created_at": "2022-05-20T14:01:22.000Z",
        "created_by": "IBMid-666000MBI9",
        "description": "AWS KMS keystore",
        "groups": [
          "Production-UK",
          "Production-DE"
        ],
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/46db7767-225b-4d41-b49f-a051107de10d",
        "id": "46db7767-225b-4d41-b49f-a051107de10d",
        "location": "eu_central_1",
        "name": "AWS KMS Keystore Name2",
        "type": "aws_kms",
        "updated_at": "2022-05-20T14:01:22.000Z",
        "updated_by": "IBMid-666000MBI9",
        "vault": {
          "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
          "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
          "name": "Example Vault"
        }
      },
    ],
    "last": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores?vault.id=5d1b7665-3652-4bc8-a1ee-3ea820919613\u0026limit=20\u0026offset=0"
    },
    "limit": null,
    "offset": null,
    "total_count": 2
  }
  ```
  {: screen}

#### ibmcloud hpcs uko keystore-create
{: #command-uko-keystore-create}

Use this command to create an internal keystore or connect to an external keystore.

```
ibmcloud hpcs uko keystore-create --uko-vault UKO_VAULT --keystore-body KEYSTORE_BODY 
```

- Command options

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko keystores` command to retrieve the UUID.

    --keystore-body ([KeystoreCreationRequest](#uko-keystore-creation-request-example-schema))
    :   Required. Properties of the keystore that you want to create or connect to. 

- Example

  ```
  ibmcloud hpcs uko keystore-create \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --keystore-body='{"type": "aws_kms", "vault": {"id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b"}, "name": "AWS KMS Keystore Name", "description": "AWS KMS keystore", "groups": ["Production-UK", "Production-DE"], "aws_region": "eu_central_1", "aws_access_key_id": "JDRUDLOFEGOIGPKJBKAX", "aws_secret_access_key": "X3nKz4KNBFPC7RcyTR3f86XbNQEZdYPQbODlCXOF"}' \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T14:52:18Z
  {
    "aws_access_key_id": "",
    "aws_region": "eu_central_1",
    "aws_secret_access_key": "",
    "created_at": "2022-05-20T14:52:18.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "AWS KMS keystore",
    "groups": [
      "Production-UK",
      "Production-DE"
    ],
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/3a8c78ac-3a52-43d6-80c0-764b7dc79e89",
    "id": "3a8c78ac-3a52-43d6-80c0-764b7dc79e89",
    "location": "eu_central_1",
    "name": "AWS KMS Keystore Name",
    "type": "aws_kms",
    "updated_at": "2022-05-20T14:52:18.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "name": "Example Vault"
    }
  }
  ```
  {: screen}

#### hpcs uko keystore-delete
{: #command-uko-keystore-delete}

Use this command to delete an internal keystore or remove a connection to an external keystore.

```
ibmcloud hpcs uko keystore-delete --id ID --uko-vault UKO_VAULT --if-match IF_MATCH
```

- Command options

    --id (string)
    :   Required. The UUID of the keystore. You can use the `ibmcloud hpcs uko keystores` command to retrieve the UUID.

    --uko-vault (string)
    :   Required.  The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko keystores` command to retrieve the UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko keystore` command to retrieve the ETag.

- Example

  ```
  ibmcloud hpcs uko keystore-delete \
      --id=0325e05e-2b25-4f13-85b2-2d7f85e54359 \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --if-match=2022-05-11T14:58:26Z
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:
  ```
  ...
  OK
  ```

#### hpcs uko keystore
{: #command-uko-keystore}

Use this command to retrieve a target internal or external keystore and its details by specifying the ID.

```
ibmcloud hpcs uko keystore --id ID --uko-vault UKO_VAULT 
```

- Command options

    --id (string)
    :   Required. The UUID of the keystore. You can use the `ibmcloud hpcs uko keystores` command to retrieve the UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko keystores` command to retrieve the UUID.

- Example

  ```
  ibmcloud hpcs uko keystore \
      --id=0325e05e-2b25-4f13-85b2-2d7f85e54359 \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T14:59:03Z
  {
    "aws_access_key_id": "",
    "aws_region": "eu_central_1",
    "aws_secret_access_key": "",
    "created_at": "2022-05-20T14:52:18.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "Updated description",
    "groups": [
      "Production-UK",
      "Production-DE"
    ],
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/0325e05e-2b25-4f13-85b2-2d7f85e54359",
    "id": "0325e05e-2b25-4f13-85b2-2d7f85e54359",
    "location": "eu_central_1",
    "name": "AWS KMS Keystore Name",
    "type": "aws_kms",
    "updated_at": "2022-05-20T14:59:03.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5d1b7665-3652-4bc8-a1ee-3ea820919613",
      "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "name": "Example Vault"
    }
  }
  ```
  {: screen}

#### ibmcloud hpcs uko keystore-update
{: #command-uko-keystore-update}

Use this command to update attributes of an internal keystore or an external keystore connection.

```
ibmcloud hpcs uko keystore-update --id ID --uko-vault UKO_VAULT --if-match IF_MATCH --keystore-body KEYSTORE_BODY 
```

- Command options

    --id (string)
    :   Required. The UUID of the keystore. You can use the `ibmcloud hpcs uko keystores`  command to retrieve the UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko keystores`  command to retrieve the UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko keystore`  command to retrieve the ETag.

    --keystore-body ([KeystoreUpdateRequest](#uko-keystore-update-request-example-schema))
    :   Required. Keystore properties that you want to update.

- Example

  ```
  ibmcloud hpcs uko keystore-update \
      --id=0325e05e-2b25-4f13-85b2-2d7f85e54359 \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --if-match=2022-05-11T14:58:26Z \
      --keystore-body='{"description": "Updated description"}' \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T14:59:03Z
  {
    "aws_access_key_id": "",
    "aws_region": "eu_central_1",
    "aws_secret_access_key": "",
    "created_at": "2022-05-20T14:52:18.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "Updated description",
    "groups": [
      "Production-UK",
      "Production-DE"
    ],
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/0325e05e-2b25-4f13-85b2-2d7f85e54359",
    "id": "0325e05e-2b25-4f13-85b2-2d7f85e54359",
    "location": "eu_central_1",
    "name": "AWS KMS Keystore Name",
    "type": "aws_kms",
    "updated_at": "2022-05-20T14:59:03.000Z",
    "updated_by": "IBMid-666000MBI9",
    "vault": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "id": "5295ad47-2ce9-43c3-b9e7-e5a9482c362b",
      "name": "Example Vault"
    }
  }
  ```
  {: screen}

#### hpcs uko keystore-status
{: #command-uko-keystore-status}

Use this command to retrieve the status of a target internal or external keystore.

```
ibmcloud hpcs uko keystore-status --id ID --uko-vault UKO_VAULT 
```

- Command options

    --id (string)
    :   Required. The UUID of the keystore. You can use the `ibmcloud hpcs uko keystores` command to retrieve the UUID.

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko keystores` command to retrieve the UUID.

- Example

  ```
  ibmcloud hpcs uko keystore-status \
      --id=0325e05e-2b25-4f13-85b2-2d7f85e54359 \
      --uko-vault=5295ad47-2ce9-43c3-b9e7-e5a9482c362b \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  {
    "health_status": "ok",
    "last_heartbeat": "2022-05-20T15:00:21.000Z",
    "message": "Ping executed successfully."
  }
  ```
  {: screen}

#### hpcs uko managed-keys-from-keystore
{: #command-uko-managed-keys-from-keystore}

Use this command to list all managed keys that are installed in the target keystore.

```
ibmcloud hpcs uko managed-keys-from-keystore --uko-vault UKO_VAULT --id ID [--algorithm ALGORITHM] [--state STATE] [--limit LIMIT] [--offset OFFSET]
```

- Command options

    --uko-vault (string)
    :   Required. The UUID of the vault where the update is to take place. You can use the `ibmcloud hpcs uko vaults` command to retrieve the UUID.

    --id (string)
    :   Required. The UUID of the keystore. You can use the `ibmcloud hpcs uko keystores` command to retrieve the UUID.

    --algorithm (string)
    :   Optional. The algorithm of the returned keys. Values that can be set are `aes` and `rsa`.

    --state (string)
    :   Optional. The state that returned keys are to be in. The default value is `active`. Values that can be set are: `pre_activation`, `active`, `deactivated`, `destroyed`.

    --limit (int64)
    :   Optional. The number of keys to retrieve. The maximum value is `1000`. The minimum value is `1`.

    --offset (int64)
    :   Optional. The number of keys to skip. The minimum value is `0`.

- Example

  ```
  ibmcloud hpcs uko managed-keys-from-keystore \
    --uko-vault=eb66ebbd-7230-4cde-89bf-17282cda5faa \
    --id=f779c44d-b90e-4917-b8b0-28d4591fefda \
    --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  {
    "first": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/f779c44d-b90e-4917-b8b0-28d4591fefda/managed_keys?limit=20"
    },
    "last": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/f779c44d-b90e-4917-b8b0-28d4591fefda/managed_keys?limit=20\u0026offset=0"
    },
    "limit": null,
    "managed_keys": [
      {
        "activation_date": "2027-07-06",
        "algorithm": "aes",
        "created_at": "2022-05-27T10:21:47.000Z",
        "created_by": "IBMid-666000MBI9",
        "description": "new description",
        "expiration_date": "2028-09-17",
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/managed_keys/ab727092-9142-46dc-bf60-e29e21589c99",
        "id": "ab727092-9142-46dc-bf60-e29e21589c99",
        "instances": [
          {
            "id": "16575d32-50cc-4079-9544-1ecd2d875865",
            "keystore": {
              "group": "Production",
              "type": "ibm_cloud_kms"
            },
            "label_in_keystore": "IBM CLOUD KEY",
            "type": "secret_key"
          }
        ],
        "label": "IBM CLOUD KEY",
        "referenced_keystores": [
          {
            "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/keystores/f779c44d-b90e-4917-b8b0-28d4591fefda",
            "id": "f779c44d-b90e-4917-b8b0-28d4591fefda",
            "name": "AWS KMS Keystore Name",
            "type": "aws_kms"
          }
        ],
        "size": "256",
        "state": "active",
        "tags": [
          {
            "name": "first-tag",
            "value": "for-IBM-CLOUD"
          }
        ],
        "template": {
          "id": "67a14437-3838-4fdf-b84d-1ed062585548",
          "name": "IBM-Cloud-Template"
        },
        "updated_at": "2022-05-27T10:21:49.000Z",
        "updated_by": "IBMid-666000MBI9",
        "vault": {
          "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/eb66ebbd-7230-4cde-89bf-17282cda5faa",
          "id": "eb66ebbd-7230-4cde-89bf-17282cda5faa",
          "name": "Test_Vault_Go_Cli"
        },
        "verification_patterns": [
          {
            "method": "ENC-ZERO",
            "value": "673A61"
          }
        ]
      }
    ],
    "offset": null,
    "total_count": 1
  }
  ```
  {: screen}

#### hpcs uko vaults
{: #command-uko-vaults}

Use this command to list all vaults in the instance.

```
ibmcloud hpcs uko vaults [--limit LIMIT] [--offset OFFSET]
```

- Command options

    --limit (int64)
    :   Optional. The number of vaults to retrieve. The maximum value is `1000`. The minimum value is `1`.

    --offset (int64)
    :   Optional. The number of vaults to skip. The minimum value is `0`.

- Example

  ```
  ibmcloud hpcs uko vaults --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  {
    "first": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults?name=VAULT\u0026limit=20"
    },
    "last": {
      "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults?name=VAULT\u0026limit=20\u0026offset=0"
    },
    "limit": null,
    "offset": null,
    "total_count": 1,
    "vaults": [
      {
        "created_at": "2022-05-20T15:27:01.000Z",
        "created_by": "IBMid-666000MBI9",
        "description": "This is an updated description",
        "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/06ce6d7e-9edb-431b-8a96-e88e8a4b266b",
        "id": "06ce6d7e-9edb-431b-8a96-e88e8a4b266b",
        "name": "VAULT",
        "updated_at": "2022-05-20T15:30:40.000Z",
        "updated_by": "IBMid-666000MBI9"
      }
    ]
  }
  ```
  {: screen}

#### hpcs uko vault-create
{: #command-uko-vault-create}

Use this command to create a vault in the instance with the specified name and description.

```
ibmcloud hpcs uko vault-create --name NAME [--description DESCRIPTION] 
```

- Command options

    --name (string)
    :   Required. A human-readable name to assign to your vault. To protect your privacy, do not use personal data, such as your name or location. The length must be between 1 and 100 characters. The value must match the regular expression `/^[A-Za-z][A-Za-z0-9#@!$% '_-]*$/`.

    --description (string)
    :   Optional. The description of the vault. The length must be between 0 and 200 characters. The value must match the regular expression `/(.|\\n)*/`.

- Example

  ```
  ibmcloud hpcs uko vault-create \
      --name='VAULT' \
      --description='This is a vault' \
      --output json
  ```
  {: pre}

- Output 

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T15:27:01Z
  {
    "created_at": "2022-05-20T15:27:01.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "This is a vault",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/06ce6d7e-9edb-431b-8a96-e88e8a4b266b",
    "id": "06ce6d7e-9edb-431b-8a96-e88e8a4b266b",
    "name": "VAULT",
    "updated_at": "2022-05-20T15:27:01.000Z",
    "updated_by": "IBMid-666000MBI9"
  }
  ```
  {: screen}

#### hpcs uko vault-delete
{: #command-uko-vault-delete}

Use this command to delete a vault from your instance. Make sure that no keys or keystores are assigned to the vault before you run this command.

```
ibmcloud hpcs uko vault-delete --id ID --if-match IF_MATCH 
```

- Command options

    --id (string)
    :   Required. The UUID of the vault. You can use the `ibmcloud hpcs uko vaults` command to retrieve the UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko vault` command to retrieve the ETag.

- Example

  ```
  ibmcloud hpcs uko vault-delete \
      --id=a88f6e06-c903-4b9f-8ee0-45bd817bf1b6 \
      --if-match=2022-05-11T14:58:26Z
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ...
  OK
  ```
  {: screen}

#### hpcs uko vault
{: #command-uko-vault}

Use this command to retrieve a vault and its details by specifying the ID.

```
ibmcloud hpcs uko vault --id ID 
```

- Command options

    --id (string)
    :   Required. The UUID of the vault. You can use the `ibmcloud hpcs uko vaults` command to retrieve the UUID.

- Example

  ```
  ibmcloud hpcs uko vault \
      --id=06ce6d7e-9edb-431b-8a96-e88e8a4b266b\
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T15:30:40Z
  {
    "created_at": "2022-05-20T15:27:01.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "This is a vault",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/06ce6d7e-9edb-431b-8a96-e88e8a4b266b",
    "id": "06ce6d7e-9edb-431b-8a96-e88e8a4b266b",
    "name": "VAULT",
    "updated_at": "2022-05-20T15:27:01.000Z",
    "updated_by": "IBMid-666000MBI9"
  }
  ```
  {: screen}

#### hpcs uko vault-update
{: #command-uko-vault-update}

Use this command to update attributes of a vault.

```
ibmcloud hpcs uko vault-update --id ID --if-match IF_MATCH [--name NAME] [--description DESCRIPTION] 
```

- Command options

    --id (string)
    :   Required. The UUID of the vault. You can use the `ibmcloud hpcs uko vaults` command to retrieve the UUID.

    --if-match (string)
    :   Required. The precondition of the update, which is the value of the ETag from the header on a GET request. You can use the `ibmcloud hpcs uko vault` command to retrieve the ETag.

    --name (string)
    :   Optional. Updated name of the vault.The length must be between 1 and 100 characters. The value must match the regular expression `/^[A-Za-z][A-Za-z0-9#@!$% '_-]*$/`.

    --description (string)
    :   Optional. Updated description of the vault. The length must be between 0 and 200 characters. The value must match the regular expression `/(.|\\n)*/`.

- Example

  ```
  ibmcloud hpcs uko vault-update \
      --id=06ce6d7e-9edb-431b-8a96-e88e8a4b266b \
      --if-match=2022-05-11T14:58:26Z \
      --description='This is an updated description' \
      --output json
  ```
  {: pre}

- Output

  The command returns the output similar to the following example:

  ```
  ETag
  2022-05-20T15:27:01Z
  {
    "created_at": "2022-05-20T15:27:01.000Z",
    "created_by": "IBMid-666000MBI9",
    "description": "This is a vault",
    "href": "https://uko.us-south.hs-crypto.cloud.ibm.com:9573/api/v4/vaults/06ce6d7e-9edb-431b-8a96-e88e8a4b266b",
    "id": "06ce6d7e-9edb-431b-8a96-e88e8a4b266b",
    "name": "VAULT",
    "updated_at": "2022-05-20T15:27:01.000Z",
    "updated_by": "IBMid-666000MBI9"
  }
  ```
  {: screen}

### {{site.data.keyword.uko_full_notm}} CLI plug-in commands schema examples
{: #uko-schema-examples}

The following schema examples represent the data that you need to specify for some command options. These examples show the data structure and include placeholder values for the expected value types. When you run a command, replace these values with the values that apply to your environment as appropriate.

#### KeyProperties
{: #uko-key-properties-example-schema}

The following example shows the format of the `KeyProperties` object.

```json
{
  "size" : "256",
  "algorithm" : "aes",
  "activation_date" : "P5Y1M1W2D",
  "expiration_date" : "P1Y2M1W4D",
  "state" : "active"
}
```
{: codeblock}

#### KeyPropertiesUpdate
{: #uko-key-properties-update-example-schema}

The following example shows the format of the `KeyPropertiesUpdate` object.

```json
{
  "size" : "256",
  "activation_date" : "P5Y1M1W2D",
  "expiration_date" : "P1Y2M1W4D",
  "state" : "active"
}
```
{: codeblock}

#### KeystoreCreationRequest
{: #uko-keystore-creation-request-example-schema}

The following example shows the format of the `KeystoreCreationRequest` object.

```json
{
  "type" : "aws_kms",
  "vault" : {
    "id" : "5295ad47-2ce9-43c3-b9e7-e5a9482c362b"
  },
  "name" : "AWS Keystore Name",
  "description" : "Example AWS KMS keystore",
  "groups" : [ "Production" ],
  "aws_region" : "af_south_1",
  "aws_access_key_id" : "BSDFWERUANLKJDN54AAS",
  "aws_secret_access_key" : "6HSz234KBjMrASFasfg5PasAFGNasg87asdgQzgs"
}
```
{: codeblock}

#### KeystoreUpdateRequest
{: #uko-keystore-update-request-example-schema}

The following example shows the format of the `KeystoreUpdateRequest` object.

```json
{
  "name" : "IBM Cloud Keystore Name",
  "description" : "Azure keystore",
  "groups" : [ "Production" ],
  "aws_region" : "af_south_1",
  "aws_access_key_id" : "BSDFWERUANLKJDN54AAS",
  "aws_secret_access_key" : "6HSz234KBjMrASFasfg5PasAFGNasg87asdgQzgs"
}
```
{: codeblock}

#### KeystoresPropertiesUpdate[]
{: #uko-keystores-properties-update-example-schema}

The following example shows the format of the `KeystoresPropertiesUpdate[]` object.

```json
[ {
  "group" : "Production"
} ]
```
{: codeblock}

#### KeystoresProperties[]
{: #uko-keystores-properties-example-schema}

The following example shows the format of the `KeystoresProperties[]` object.

```json
[ {
  "group" : "Production",
  "type" : "ibm_cloud_kms"
} ]
```
{: codeblock}

#### Tag[]
{: #uko-tag-example-schema}

The following example shows the format of the `Tag[]` object.

```json
[ {
  "name" : "exampleString",
  "value" : "exampleString"
} ]
```
{: codeblock}

#### VaultReferenceInCreationRequest
{: #uko-vault-reference-in-creation-request-example-schema}

The following example shows the format of the `VaultReferenceInCreationRequest` object.

```json
{
  "id" : "5295ad47-2ce9-43c3-b9e7-e5a9482c362b"
}
```
{: codeblock}
