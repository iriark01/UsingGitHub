Hello Oulu,

As promised, here is a small guide to using MD, GitHub and docs.mbed.org. Please remember that we're still experimenting ourselves, and there are no hard rules; whatever works best for your team is what you should do.

#The GitHub Client

The easiest way (for me) is to work with the GitHub client on my computer, not through the website itself.

I understand that Rob set you up with GitHub users. So all you need now is the client for [Mac](https://mac.github.com/) or [Windows](https://windows.github.com/). Install and enjoy. 

#Creating a Repo on GitHub

The easiest way:

- Create a folder on your computer.

- Drag-and-drop it to the GitHub client.

![Drag and drop](/Images/NewRepo.png)

-  You'll be asked if you want to create a repo. The answer is "yes".

- The new repo is created under *Other*. 

- Add a commit comment to it. Please remember that people can see this.

![New repo](/Images/RepoInOther.png)

- Click **Commit to master**. GitHub will then tell you that you have no new changes, but you have one unsynced change. 

![Publishing](/Images/Publish.png)

- Click **Publish**.

![Pushing](/Images/Push.png)

- Name your repo and add a description. If you created more than one GitHub account, make sure you're publishing to the right one.

- When the push is done, your repo will move to the ••GITHUB•• folder in your client. On GitHub, you'll be able to see all of your files.

- From now on it's very simple; any change you make in the folder will appear in the GitHub client. Commit and sync when you're ready.

Click on any MD file to see it on GitHub. It should render pretty well, including images.

#Building a TOC

GitHub doesn't give you a TOC, but docs.mbed.org does. However, the table of contents that's automatically generated for multi-file repos is next to useless, especially if you use folders to create a decent tree. So we need to create a TOC file. In the specific theme we're using (mkdocs), that's a YML file.

You don't have to have a YML file if you don't need a TOC, but if you build it - it must be built correctly or the whole repo will refuse to build on mbed.docs.org (GitHub doesn't build your docs, so it won't warn you that the YML is wrong).

The YML:

- Must be called **mkdocs.yml**.

- Must sit in the root directory of your repo.

- Must have a site name listed in it (see below for an example); the repo will not build without this. 

- The first file it looks for is **index.md**, which should sit next to it in the root. On docs.mbed.org this will be your repo's home page, so usually it will be some short introduction to the rest of the repo.

- The YML then creates a page list that gives each file a location in the tree and a name.

So a YML has:

	site_name: whateveryouwant

	pages:
	- ['index.md', 'Name of your choosing']
	- ['Folder/file.md', 'TOC Folder Name', 'Name for the page']
	- ['SomeOtherFolder/somefile.md', 'TOC Folder Name', 'Name for this page']

The folder and pages will be listed in the TOC in the order in which you listed them in the YML.

Note that the YML allows you to build a TOC that is completely disconnected from your file structure. You can:

- Give a page a title that is not derived from the file's name:

	['index.md', 'Name of your choosing']

- Give the section a title that is not derived from the folder's name:

	['Folder/file.md', 'TOC Folder Name', 'Name for the page']

- Combine pages from different folders under the same section, by giving them identical section names:

	['**Folder**/file.md', '**TOC Folder Name**', 'Name for the page']
	['**SomeOtherFolder**/somefile.md', '**TOC Folder Name**', 'Name for this page']

Be careful with your spacing - it doesn't build if you use spaces it's not looking for. It's one line break between **pages* and the page list, and one line break between each page entry.

You can see an example of all of these in the BLE repo: https://github.com/iriark01/BLEIntros. You can download that YML and use it as a template, if you want. Compare it to the built version on [readthedocs](http://ble-intros.readthedocs.org/en/latest/).

The YML has some other abilities, if [you're interested](http://www.mkdocs.org/user-guide/configuration/).

#Buildling on docs.mbed.org

- Log into docs.mbed.org with your **developer.mbed.org** credentials.

![Logging in](/Images/DocsLogin.png)

- You'll be taken to your dashboard. Click **Import a Project**.

![Import](/Images/Import.png)

- You get two importing options. Click **Manually Import Project**.

![Manually import](/Images/ManuallyImport.png)

- Name your project and enter the GitHub repo URL.

![Project details](/Images/ProjectDetails.png)

- Don't worry about the other options. Click **Next**.

- You'll be taken to the project page.

- The project tries to build a first version as soon as it's created. Click **Builds** to see the build's progress. 

![Project home page](/Images/ProjectHome.png)

When the build is done, you can click **View Docs** to see your project. 

Please note that docs.mbed.org is not fully live. You can review your docs on GitHub, but if you want to see the full thing (with the TOC), you'll probably need to use **Read the Docs**.

#Using Read the Docs

docs.mbed.org is based on Read the Docs and they both use the same rendering mechanism, so it's a perfect mirror of what you'll eventually get on docs.mbed.org.

- Create an [account](https://readthedocs.org/accounts/signup/).

- The rest of the process is like docs.mbed.org - you import your project from GitHub, build and view the docs.

#Relative Links

You can use relative links for MD, but they're not what you might expect:

- For an image, the link is pretty straight-forward. For example, the links for the images in this MD are all **/Images/Imagename.png**.

- For a file, the link is a little odd: it's **/Folder/File/**, without the filetype specification. 

The links are relative to the repo, not the current folder. So even if your MDs are in the same subfolder, you'll need to include the subfolder in the link. For example (from the BLE intro), from the file */GettingStarted/DevIntro.md* I link to */GettingStarted/DesignersIntro/*.
