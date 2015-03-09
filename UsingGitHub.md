#Using MD, GitHub and docs.mbed.org

Hello Oulu,

As promised, here is a small guide to using MD, GitHub and docs.mbed.org. Please remember that we're still experimenting ourselves, and there are no hard rules: whatever works best for your team is what you should do.

#The GitHub Client

The easiest way (for me) is to work with the GitHub client on my Mac, not through the website itself.

I understand that Rob set you up with GitHub users. So all you need now is the client: [Mac](https://mac.github.com/) or [Windows](https://windows.github.com/). Install and enjoy. 

#Creating a Repo on GitHub

The easiest way:

- Create a folder on your computer.

- Drag-and-drop it to the GitHub client.

![Drag and drop](/UsingGitHub/Images/NewRepo.png)

-  You'll be asked if you want to create a repo. The answer is "yes".

- The new repo is created under *Other*. 

- Add a commit comment to it. Please remember that people can see this.

![New repo](/UsingGitHub/Images/RepoInOther.png)

- Click **Commit to master**. GitHub will then tell you that you have no new changes, but you have one unsynced. 

![Publishing](/UsingGitHub/Images/Publish.png)

- Click **Publish**.

![Pushing](/UsingGitHub/Images/Push.png)

- Name your repo, and add a description. Note that you can now choose which account it goes to.

- When the push is done, your repo will move to the ••GITHUB•• folder in your client. On GitHub, you'll be able to see all of your files.

- From now on it's very simple; any change you make in the folder will appear in the GitHub client. Commit and sync when you're ready.

#The MD

Note that the MDs render differently on GitHub and docs.mbed.org

#The YML

The table of contents that's automatically generated is next to useless, especially if you use folders to create a decent tree. So we need to create a TOC file. In the specific theme we're using, that's a YML file.

The YML requires three things:

- It must be called **mkdocs.yml** and sit in the root directory of your repo.

- It must have a site name listed in it; the repo will not build without this. 

- The first file it looks for is **index.md**, which should sit next to it in the root. This is the homepage of your docs, so usually it will be some short introduction to the rest of the repo.

So a YML has:

	site_name: whateveryouwant

	pages:
	- ['index.md', 'Name of your choosing']
	- ['Folder/file.md', 'TOC Folder Name', 'Name for the page']
	- ['SomeOtherFolder/file.md', 'TOC Folder Name', 'Name for this page']

Note the following:

- Your TOC is not committed to the folder names you gave in your tree. So even though the folder is called Folder, its TOC name can be anything you want.

- You can pull pages from different folders into the same TOC section by giving their entries the same TOC Folder Name; no need to copy them between folders.

- The folder and pages appear in the order in which you list them in the YML.

- Be careful with your spacing - it doesn't build if you use spaces it's not looking for. It's one line break between **pages* and the page list, and one line break between each page entry.

You can see an example of all of these in the BLE repo: https://github.com/iriark01/BLEIntros. You can download that YML and use it as a template, if you want. Compare it to the built version on [readthedocs](http://ble-intros.readthedocs.org/en/latest/).

The YML has some other abilities, if [you're interested](http://www.mkdocs.org/user-guide/configuration/).

#Buildling on docs.mbed.org

- Log into docs.mbed.org with your developer.mbed.org credentials.

![Logging in](/UsingGitHub/Images/DocsLogin.png)

- You'll be taken to your dashboard. Click Import a Project.

![Import](/UsingGitHub/Images/Import.png)

- You get two importing options. Pick **Manually Import Project**.

![Manually import](/UsingGitHub/Images/ManuallyImport.png)

- Name your project and enter the GitHub repo URL.

![Project details](/UsingGitHub/Images/ProjectDetails.png)

- Don't worry about the other options. Click **Next**.

- You'll be taken to the project page.

- The project tries to build a first version as soon as it's created. Click **Builds** to see the build's progress. 

![Project home page](/UsingGitHub/Images/ProjectHome.png)

When the build is done, you can click **View Docs** to see your project. 

#Readthedocs

docs.mbed.org is based on Read the Docs, and that is where I build my projects to see them when 

