# F5 BIG-IP Migration Assistant Setup Guide
This guide walks you through the entire process for setting up F5® BIG-IP® Migration Assistant.

## Downloading and installing the software

### Windows

Run the executable on your Windows machine.

### OSX

Open the **dmg** file on your Mac machine and drag the **F5 BIG-IP Migration Assistant** icon into the Applications folder.

### Linux

Open the **.deb** file on your Linux desktop.

## Preparation

### Obtaining the BIG-IP master key password

You must know the master key password of the source device before setting up Migration Assistant. If you do not know the password, you must set the password on the source device before you start the setup process.  

For information about updating the device's master key, refer to [K9420: Installing UCS files containing encrypted passwords or passphrases](https://support.f5.com/csp/article/K9420).

### Importing UCS files (BIG-IP 12.1.0 and later)

If your source device is running 12.1.0 or later, you can use Migration Assistant to automatically generate and import the UCS file. To do so, perform the following procedure:

1. In Migration Assistant, click the **BIG-IP Devices** tab.
2. Click **Add Device**.
3. Enter the management IP address of the BIG-IP device, and the admin username and password. If the BIG-IP device is using a self-signed certificate, clear the **Verify server identity** check box.
4. To add the device, click **Save Device**.
5. Click the **UCS Archives** tab.
6. Click **New Archive**.
7. For **BIG-IP Device**, select the BIG-IP device you added in step 4.
8. Enter a descriptive name in the **Archive Name** field.
9. In the **Master Key** field, if you know the master key, enter it here. Otherwise, elect to reset the master key and enter a passphrase. Make sure you choose a strong passphrase.
10. Click **Generate Archive**.

### Importing UCS files (BIG-IP 11.1.0 - 11.6.x, and 12.0.0)

Migration Assistant cannot generate UCS files on these BIG-IP versions, but you can generate a UCS file manually and import it to Migration Assistant.

For more information, refer to [K4423: Overview of UCS archives](https://support.f5.com/csp/article/K4423).

Once you've generated the archive, perform the following procedure: 

1. Download the UCS file to your desktop.  
2. In Migration Assistant, click the **UCS Archives** tab.
3. Click **New Archive**.
4. Click the **Select UCS** tab.
5. Choose the UCS file and type in the master key for the UCS file.
6. Import the file by clicking **Select Archive**.

## Performing a migration

_**Important:** You can only migrate UCS files to devices running 12.1.3 and later, or 13.1.0 and later_.
_**Important:** If migrating to a vCMP guest, you must have VLANs already configured in the host to support incoming configuration_.

1. Power down the old device, start the new device, and give it the same management IP address.
2. In the **Platform Migration** tab, click **New Migration**.
3. In the **Source Archive** field, select the archive that you generated.
4. In the **Target Device** field, select the target device.
5. Click **Begin Migration**.

The status indicator at the top of the application will notify you of progress. You can perform multiple migrations simultaneously.

If the migration is successful, the progress indicator migration row will disappear. You can click the information icon to see the migration results.

### Confirming the migration on the target device

1. Depending on your network configuration, you may need to force the old device offline.
2. Log in to the BIG-IP device and verify all configuration changes are complete.
3. You may need to reconfigure VLANs and interface mappings, or any configuration elements listed in [K82540512: Overview of the UCS archive platform-migrate option](https://support.f5.com/csp/article/K82540512)
4. Perform traffic testing of your new BIG-IP device to verify that it is working properly.

## Support

If you need support for F5 BIG-IP Migration Assistant, refer to the Migration Assistant forum at [F5 DevCentral](https://devcentral.f5.com), or file an [Issue](https://github.com/f5devcentral/f5-big-ip-migration-assistant/issues).

If the BIG-IP device encounters an error loading the UCS file and you have a valid support contract, you can access support at [AskF5](https://support.f5.com/csp/home).

[Back to README](README.md)
