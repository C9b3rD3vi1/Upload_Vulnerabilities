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

When you terminate your instance of the upload vulns target machine, make sure to remove this line!

It goes without saying that you will not get the same IP address if you redeploy the target machine later. This means that any existing entries in your hosts file when you redeploy will point at the wrong address (ergo, connectivity error). If you add a duplicate line without removing the original, as mentioned above, you will also get a connectivity error. Removing it as soon as you terminate the machine gives you a clean slate and removes these possibilities for error.

The ability to upload files to a server has become an integral part of how we interact with web applications. Be it a profile picture for a social media website, a report being uploaded to cloud storage, or saving a project on Github; the applications for file upload features are limitless.

Unfortunately, when handled badly, file uploads can also open up severe vulnerabilities in the server. This can lead to anything from relatively minor, nuisance problems; all the way up to full Remote Code Execution (RCE) if an attacker manages to upload and execute a shell. With unrestricted upload access to a server (and the ability to retrieve data at will), an attacker could deface or otherwise alter existing content -- up to and including injecting malicious webpages, which lead to further vulnerabilities such as XSS or CSRF. By uploading arbitrary files, an attacker could potentially also use the server to host and/or serve illegal content, or to leak sensitive information. Realistically speaking, an attacker with the ability to upload a file of their choice to your server -- with no restrictions -- is very dangerous indeed.

The purpose of this room is to explore some of the vulnerabilities resulting from improper (or inadequate) handling of file uploads. Specifically, we will be looking at:

    Overwriting existing files on a server
    Uploading and Executing Shells on a server
    Bypassing Client-Side filtering
    Bypassing various kinds of Server-Side filtering
    Fooling content type validation checks

## General Methodology
