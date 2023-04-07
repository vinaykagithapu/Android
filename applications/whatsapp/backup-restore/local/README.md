# WhatsApp - Backup/Restore - Local
- We can backup/restore whatsapp chat history from local storage(without google drive). 

# Getting Started
## Requirements
1. File manager (Files by Google).
2. WhatsApp
3. Internet connection

## BackUp WhatsApp Chat
1. WhatsApp will backup the chat to a specific location in filesystem.
2. Location may vary between devices and android versions.
3. Open **Files by Google** > **Internal storage** > **Android**
4. **media** > **com.whatsapp** > **WhatsApp** > **Databases**
```shell
Internal-storage/Android/media/com.whatsapp/WhatsApp/Databases/

or

Internal-storage/WhatsApp/Databases/

or 

sdcard/Android/media/com.whatsapp/WhatsApp/Databases/

or 

sdcard/WhatsApp/Databases/
``` 
5. Within the above locations, encrypted message databases files are stored. 
```shell
msgstore-2023-04-01.1.db.crypt14
msgstore-2023-04-02.1.db.crypt14
msgstore-2023-04-03.1.db.crypt14
msgstore-2023-04-04.1.db.crypt14
msgstore-2023-04-05.1.db.crypt14
msgstore-2023-04-06.1.db.crypt14
msgstore.db.crypt14
```
6. Need to choose a **latest database file**. (Ex: **msgstore-2023-04-06.1.db.crypt14**) 

>_**NOTE :**_ msgstore-2023-04-06.1.db.crypt14 database file contains chats upto date include in filename. It doesn't include chat from the next day 2AM. 

>_**WARNING :**_ It doesn't backup media like images, docs, photos, videos etc. Instead it will backup indexes of media.

7. Should **backup** the latest database file to any of the **storage service** like S3, Google Drive, Azure Blob etc. 

## Restore WhatsApp Chat
1. **Uninstall** WhatsApp, this will delete entire filesystem of WhatsApp.
2. Now **download** the backed up file (Ex: **msgstore-2023-04-06.1.db.crypt14**)
3. **Rename** it as **msgstore.db.crypt14**
4. **Install** WhatsApp, **open** it > **[*] English** > **Agree and continue**. (don't go beyond this setup)
5. Open **Files by Google** > **Internal storage** > **Android** > **media** > **com.whatsapp** (in my scenario)
6. Within **com.whatsapp** create **WhatsApp** directory
7. Within **WhatsApp** create **Databases** directory
8. Now copy the **msgstore.db.crypt14** to **Databases** directory.
9. Open **WhatsApp** > **Enter phone number** > **Next** > **Allow contacts**
10. Will get **Restore backup** screen stating as below, click on **Restore** > **Next**
```console
Backup found

Restore your messages and media from your phone's internal storage. If you don't restore now, you won't be able to restore later.
```
