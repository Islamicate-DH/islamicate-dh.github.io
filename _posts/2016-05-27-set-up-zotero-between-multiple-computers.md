---
layout: post
title: Set Up a Shared Zotero Library Between Two Computers
---

Zotero is one of the most robust citation management systems out there---open source, free, and great at grabbing metadata and files straight from the web---and with a little tweaking, it can become a great way to organize and maintain a large library of PDFs. For many users, the default settings are perfectly fine, but there are some potential drawbacks that some (such as myself) may wish to address:

- Sharing PDFs between your computers may become dicey if your library becomes too big. One option is to simply pay $20/year to get 2GB of storage space on Zotero, or you can pair it up with a service like Box or Google Drive through the WebDAV protocol (see Zotero's [sync documentation](https://www.zotero.org/support/sync); more links at the bottom of this page). However, if you opt for one of these solutions, you may be turned off by another issue:
- By default, Zotero puts each attachment in a separate folder, buried deep within its directory system and assigned a random number. This is intentional; to protect your data, you're not supposed to be able to easily find and manipulate your files directly. However, if you like to access your files easily through the Finder, this can be annoying.

There is one very easy way you can move your Zotero attachments to another folder where they are visible to the naked eye, so to speak, and that is the [ZotFile](http://zotfile.com/) plugin, but ZotFile, rather unavoidably, does not play well with the WebDAV solution mentioned above. It is possible, however, to set up your Zotero database using ZotFile to link all your attachments to a shared folder such as DropBox or Box. This is the route I opted for, and with a little trial and error, I found a system that is working very well for me (almost perfect, but not quite, to quote Shel Silverstein). In the following post, I will walk you through the steps I did to configure Zotero on multiple machines sharing a single library; I cannot guarantee this will work on every computer, but if your setup exactly matches what I describe below, it should work.

## Prerequisites ##

Before diving in and making a mess of things, first check to make sure you meet the following conditions, or at least are aware of what issues you might have to address if you do not:

1. I am using two Macs---a desktop and a laptop---and I am using the same username for both machines. This is important because it means that my **directory path** for attachment storage will be identical on both computers; i.e. they will both say `/Users/thisismyusername/DropBox/Zotero`. If your username varies from computer to computer, your path will not be the same, and this may make the following tutorial unusable for you; or at least you will have to do some additional steps to make sure your attachments are pointed towards exactly the same location.
2. Going back to that first point, this was done and tested on Mac OS X. I am sure it will work the same for Ubuntu or other Unix-based systems, but I am not familiar enough with Windows to vouch for it. If you use Windows, make a backup (which you should do anyway) and proceed at your own risk. (There is a link at the bottom of this page that may be more helpful for you.)
3. Set up a user account with [zotero.org](https://www.zotero.org/), if you don't have one yet. 
4. Finally, set up an account with a service that syncs a folder with online storage: this could be DropBox, Box, or Google Drive, to name three of the most well-known options. Pick your favorite, navigate to that directory, and create a folder to store your files. (I'm calling it "Zotero" for the sake of this tutorial, but of course you can call it whatever you want.)

## Step 1: Set Up Your Library ##

If you already have a working Zotero library, start by **backing it up** (if you don't know how to do that, go to [Zotero's guide to backing up](https://www.zotero.org/support/zotero_data) and follow the instructions). If not, just open up vanilla Zotero, hop onto J-Stor, and download a couple articles to have a working sample to try out.

Once you have your library set up and backed up, you'll want to download the ZotFile plugin. Go to [zotfile.com](http://zotfile.com/) and follow the instructions for installation (these will vary depending on whether you prefer using Zotero Stand-Alone or the Zotero plug-in with Firefox).

Now that ZotFile is installed, time to set up your preferences! There are **two sections** where we will be adjusting our preferences, so make sure to hit them both. Let's start with ZotFile: click on the settings button in Zotero, select "ZotFile preferences," and follow the steps below:

1. In _General Settings_, you want to set a **Custom Location** for the location of your files. I'm using Box, so I get `/Users/myusername/Box Sync/Zotero`. I also tick the "Use subfolder" option and fill the box with `/%A/`; this will sort all my files into subdirectories arranged alphabetically by last name, making it very easy for me to navigate to the 'S' folder to look up 'Smith'. (Again, you can set up your subfolder schema---if you want one at all---however you like; this is just what I did.)
2. In _Tablet Settings_, I did not change a thing. I'm not dealing with tablets. (But if you are, investigate this further, it's a great feature.)
3. In _Renaming Rules_, I tweaked the format to read `{%a} {%y} - {%t}`, and I also unchecked the "Truncate title" option. These are cosmetic; you can choose whatever naming system you like (see the [ZotFile renaming rules](http://zotfile.com/#renaming-rules)) or stick with the defaults, which are very good.
4. In _Advanced Settings_, tell Zotfile to _always_ automatically rename new attachments (this simplifies your life). You shouldn't have to change anything else, but I did ask ZotFile to "Remove diacritics from filename" to make searching easier, and I added the `djvu` suffix to the list of filetypes it will work with, since I do like the .djvu format. These changes, too, are of secondary importance.

To review, the only really important thing we have done so far is set the **Custom Location** for our files in a directory that syncs to the cloud, so that we can access them from other computers when the time comes. Now, on to the **Regular Zotero preferences** (click on the settings button and select 'Preferences').

1. In _General_, you don't need to change anything (but I like to uncheck automatic snapshots and tags).
2. In _Sync_, enter the Username and Password for your Zotero account, and make sure "Sync automatically" and "Sync full-text" is checked. **Uncheck** the two options under "File Syncing" ('Sync attachment files in My Library' and 'Sync attachment files in group libraries'); ZotFile is taking care of this part.
3. The _Search_, _Export_, and _Cite_ menus you can leave alone.
4. In _Advanced_, click on the sub-category of "Files and Folders" and **set your Base directory to be the same as what you set in ZotFile**---in our example, it will be `/Users/myusername/Box Sync/Zotero`. Under "Data Directory Location", leave it set as your profile directory. The profile directory does not contain any files you need to mess with, and can remain hidden. The one thing you must **never** do is put this directory in a DropBox (etc.) folder; that will corrupt your database over time. Just leave it happy where it is.

Hit `OK`. We have set our preferences and done most of the work. Now it's time to test out ZotFile. Select **all** of the files in your library (it matters not whether it's 10 or 1000), right-click, and select `Manage Attachments --> Rename Attachments`. ZotFile will do its magic and rename and relocate your entire library to the directory you have designated using the system you specified---and it can do a huge library in just a minute or two. Go to your Zotero directory just to make sure the files are there, and they should start automatically uploading into the cloud. If everything looks good, go back to the main Zotero window and hit the green sync button (in the upper right corner of the window, it looks like an arrow turning clockwise); this will upload your database (_sans_ files) to your online account. If you want to make sure it's there, you can hop back onto [zotero.org](https://www.zotero.org/), and you should see your database under 'My Library'.

To recap, here's what you've done so far: you're using Zotero's sync capability to maintain an online database of all your references and files, and meanwhile ZotFile has taken over the work of managing where those files get stored. A simple division of labor.

If everything looks good, you're basically done: syncing new computers to this library can be done relatively quickly and easily. if you have a large library you want to make sure doesn't get screwed up, make a copy of your profile directory and keep it somewhere as a backup. Now, open up a clean install of Zotero on your second machine, install ZotFile, and **set up the Zotero and ZotFile preferences EXACTLY as they are on your primary machine**. Once the preferences are set up **and match perfectly** (can I stress this enough?) hit the green sync button on the new install of Zotero, and a great thing will happen:

- Zotero will grab all your database info and metadata from its server, duplicating your library into your second computer;
- ZotFile will tell it to look for the linked files in the Dropbox/GoogleDrive/Box folder you specified.

What's great about this system is that you can now effectively use Zotero from either machine. If you add a new article while on the road, ZotFile will move it to DropBox (etc.) to be shared with your main computer, and Zotero will update its servers; so that when you get back home and open Zotero, the PDF will be waiting for you in your DropBox and your Zotero library will have synced up to the most recent version. Even your annotations will be shared across machines, and if you want to share a file with a friend, DropBox or Box or Drive makes it easy. I'm very happy with this setup. There is only one issue you should know about that I am not sure how to address: if you delete a file in Zotero, ZotFile will **not** delete it from your hard drive. In other words, because of our division of labor, you have to delete the file twice, so to speak: first you delete the entry from Zotero to remove it from the database, then you have to go to your DropBox folder and delete the actual PDF (fortunately, there is no harm if you just leave it, but it clutters things up).

I hope this is helpful! Let me know if you see any potential problems or have any suggestions as to how I can improve it.

## Links ##

Here are the major links I mention in this post, in addition to a number of tutorials that helped me out quite a lot to figure this out.

- [Zotero's sync documentation](https://www.zotero.org/support/sync): a useful overview of the process.
- [Zotfile](http://zotfile.com/): the plug-in that makes it all happen.
- [Link your Zotero files](https://mannlib.cornell.edu/news/link-your-zotero-files-cornell-box): a useful tutorial from library at Cornell University.
- [Syncing Zotero databases](https://community.box.com/t5/Help-Forum/Syncing-Zotero-database-across-Mac-OS-Windows-7-and-Windows-10/td-p/10216): from the Box forums, was useful for me to think through how I would do it.
- [Syncing Zotero files with WebDAV](http://academic.bancey.com/syncing-zotero-files-with-webdav-from-box/): a basic tutorial to show you how to set up Zotero with Box using the WebDAV protocol. This solution is fine, but you don't get the file renaming goodness that comes with ZotFile.
- [Setting up a portable library with Zotfile](http://freecity.commons.gc.cuny.edu/2013/12/14/setting-up-a-portable-library-with-zotfile/): offers a slightly different approach, but it was helpful for me to think through mine.
- [Syncing Zotero with Dropbox and several computers](http://remembereverything.org/syncing-zotero-with-dropbox-and-several-computers/): specifically geared for Windows users.