# Upload_Vulnerabilities

Tutorial room exploring some basic file-upload vulnerabilities in websites

## Introduction

First up, let's deploy the machine to give it a few minutes to boot.

Once you've clicked deploy, you'll need to configure your own computer to be able to connect.

If you've successfully deployed the machine then the following code blocks will already have the IP address filled in. If any of them have "MACH​INE_IP" in them, then you still need to deploy the machine, and the following instructions will not work.

Using your favourite text editor in an administrative session, open the hosts file on your device.

On Linux and MacOS the hosts file can be found at ***/etc/hosts***.
On Windows the hosts file can be found at ***C:\Windows\System32\drivers\etc\hosts**.

On Linux or MacOS you will need to use sudo to open the file for writing. In Windows you will need to open the file with ***Run as Administrator***.

Add the following line in at the end of the file:

    MACHINE_IP    overwrite.uploadvulns.thm shell.uploadvulns.thm java.uploadvulns.thm annex.uploadvulns.thm magic.uploadvulns.thm jewel.uploadvulns.thm demo.uploadvulns.thm

Note: ***If you have done this step before then you must remove the previous entry. There should only ever be one line in the file that contains the above URLs. For example, the following example will not work:***

***10.10.10.10    overwrite.uploadvulns.thm shell.uploadvulns.thm java.uploadvulns.thm annex.uploadvulns.thm magic.uploadvulns.thm jewel.uploadvulns.thm demo.uploadvulns.thm***

***MACHINE_IP    overwrite.uploadvulns.thm shell.uploadvulns.thm java.uploadvulns.thm annex.uploadvulns.thm magic.uploadvulns.thm jewel.uploadvulns.thm demo.uploadvulns.thm***

