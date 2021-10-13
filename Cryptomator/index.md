Cryptomator
===

```{toctree}
:hidden:

Cryptomator_Architecture
```

```{image} _images/cryptomator.png
:alt: Send Command
:width: 400px
```

Support for client-side encryption with [Cryptomator](https://cryptomator.org/) interoperable Vaults to secure your data on any server or cloud storage.

```{image} _images/Browse_Cryptomator_Vault.gif
:alt: Send Command
:width: 600px
```

The client-side encryption feature in Cyberduck and Mountain Duck is based on the excellent concepts and work of [Cryptomator](https://cryptomator.org/). Cryptomator is free and open-source software. Since Cyberduck is also open-source software anyone is able to audit the source code. That means no security by obscurity, no hidden backdoors from third parties, no need to trust anyone except yourself.

Compared to other client-side-encryption solutions the Cryptomator based approach yields a few crucial advantages:

- in addition to file content encryption also file and directory names are encrypted and directory structures obfuscated
- no online services, no subscriptions, no accounts
- no need to share your cloud storage provider credentials

# Create new Vault

You can create a new Vault directory anywhere on your remote storage. This will initialize the Vault with a `masterkey.cryptomator`. A backup of the master key file (`masterkey.cryptomator`) is saved in user defaults. The encrypted keys in `masterkey.cryptomator` are not more sensitive than the encrypted files in the vault. For technical aspects, refer to [Masterkey Derivation](https://docs.cryptomator.org/en/latest/security/architecture/#masterkey-derivation).

`````{tabs}
````{group-tab} macOS

Choose *File → New Vault…* to create a new Vault. 

```{image} _images/New_Encrypted_Vault_File_Menu_Option.png
:alt: Send Command
:width: 400px
```

````
````{group-tab} Windows

- Choose *New Vault…* from the Finder Extension toolbar or context menu using right-click in Finder or Windows Explorer.

```{image} _images/Mountain_Duck_Create_New_Vault_Finder_Extension.png
:alt: Send Command
:width: 400px
```

```{image} _images/Mountain_Duck_Create_New_Vault_Windows_Explorer.png
:alt: Send Command
:width: 400px
```

- Choose a name for the Vault folder and a passphrase to secure the Vault.

```{image} _images/Create_New_Vault.png
:alt: Send Command
:width: 400px
```

````
`````

# Unlock Vault

## Discovery

When `Preferences → Cryptomator → Auto detect and open vault in browser` is enabled, opening a directory in the browser that is a Cryptomator Vault, a prompt is displayed to unlock the Vault using the provided passphrase and decrypt the directory and filenames. If you cancel the prompt, the encrypted Vault content is displayed.

`````{tabs}
````{group-tab} macOS

```{image} _images/Mountain_Duck_Unlock_Vault.png
:alt: Send Command
:width: 400px
```

````
````{group-tab} Windows

```{image} _images/Mountain_Duck_Unlock_Vault_Windows.png
:alt: Send Command
:width: 400px
```

````
`````

## Manual

````{tabs}
```{group-tab} Cyberduck

Choose the *Cryptomator* button in the toolbar or the option in the *File* menu to unlock and lock a Cryptomator Vault.

```
```{group-tab} Mountain Duck

Lock and unlock vaults within the Finder or Windows Explorer using the context menu:

`Mountain Duck → Cryptomator → Lock Vault`
`Mountain Duck → Cryptomator → Unlock Vault`

```
````


## Save Passphrase

You can check *Add to Keychain* to save the passphrase to open the vault with the master key file in your login keychain. The checkbox is disabled by default. Another application that wants to access the Vault passphrase from the login keychain will trigger a permission prompt.

```{image} _images/Keychain_Access_Crpytomator_Passphrase.png
:alt: Send Command
:width: 400px
```

`````{tabs}
````{group-tab} macOS

Manage your passwords with *Keychain Access.app* on Mac. Refer to [Keychain for Mac: Keychain Access overview](https://support.apple.com/kb/PH20093?locale=en_US).

````
````{group-tab} Windows

Passwords are saved in the *Credential Manager*. You can view and delete your saved login information in *Control Panel → User Accounts → Credential Manager → Windows Credentials*.

````
`````

## File Transfers

File transfers require you to unlock the Vault again unless you have chosen to save your Vault passphrase in the keychain.

# Browser

You can open and browse multiple Vaults on a server in a single browser window. For each Vault to be opened you will be prompted to enter your passphrase to decrypt the filenames. Decrypted filenames when browsing a Vault will show a padlock overlay icon.

```{image} _images/Cryptomator_Vault_Browser.png
:alt: Send Command
:width: 400px
```

## Moving Files Into Vault

You can move files from and to the Vault. Because files need to be encrypted or decrypted respectively they pass through your local computer and cannot be moved on the server-side.

```{note}
The Vault must be unlocked before you move files to it, otherwise the files won't be encrypted.
```

## Access Vaults on Local Disk

Both [Cyberduck](https://cyberduck.io/) and [Mountain Duck](https://mountainduck.io/) support browsing your local disk to access Vaults created on your computer. Create a new [bookmark](../Cyberduck/Bookmarks) to connect to your local disk.

```{image} _images/local_disk_connection.png
:alt: Send Command
:width: 400px
```

In your local disk connection, you can access all directories which are saved on your local disk. This includes for example your local synchronized [Dropbox](../Protocols/Dropbox), [Google Drive](../Protocols/Google_Drive) and [OneDrive](../Protocols/OneDrive) directories.

````{admonition} Access a Cryptomator Vault on local disk on the example of Dropbox
:class: note

1. Navigate to the Dropbox directory and open the subdirectories until you reach your Cryptomator Vault.
2. Double click your vault.
3. Type your set password in the password box. If you want you can save the password for easier access to this directory for further usage.

```{image} _images/access_Cryptomator_vault_Mountain_Duck.png
:alt: Send Command
:width: 400px
```

```{image} _images/access_Cryptomator_vault_Cyberduck.png
:alt: Send Command
:width: 400px
```

4. Click the Continue button and your Vault should open.

````

# Known Limitations

- Changing the Vault passphrase is currently not supported.
- To delete a Vault it cannot be unlocked. Choose *Cancel* in the vault password prompt to skip unlocking the Vault after selecting the Vault folder for delete.

# Security Architecture

See [Security Architecture Overview](https://docs.cryptomator.org/en/latest/security/architecture/#).

# Preferences

## Auto Detect

Uncheck *Preferences → Cryptomator → Auto detect and open Vault in browser* to disable opening Vaults by default when opening the Vault directory in the browser.

# References

See [Encryption Security Architecture](Cryptomator_Architecture).