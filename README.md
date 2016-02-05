# sr-release

Tool for easy software release management. It generates CHANGELOG.md file based on git commits and creates git tags.
 In the process the tool is pushing the changes to the remote origin. 
 

# Typical usage 

Run sr-release in the directory of your repo code.

## Detecting non-commited files

```
$ sr-release 
 M packages.ini
Please commit changes before you can generate changelog

```
In the example above sr-released detected that there are non-commited files and the process of software release cannot be continued.


## Generating CHANGELOG.md
If all files are commited we run the tool again form the main directory of the local project copy. 

```
$ sr-release
Changelog exist. File 'CHANGELOG.md' will be updated

```

The tool generates changes and saves them into CHANGELOG.md under section with headline "New Version Tag do not change this line". See below:

This is the moment when the operator of the tool can update the changelog. He needs just after generating changelog go end edit the file in section which was just added. 
 
## Releasing software
When everything is ready and CHANGELOG.md was updated we just need to run the tool again and now the process will be ready for actual tagging and releasing the code.
The process should look like below. 

```
$ sr-release
Have you checked and updated CHANGELOG.md file? [y/N] y
Starting procedure of new release

The lastest tag is: 1.0.0
Enter the new tag and press [ENTER] 1.0.1
Updating CHANGELOG.md by the new tag 1.0.1
[develop 19ff088] Releasing new version 1.0.1
 1 file changed, 5 insertions(+)
Would you like to push the changes to the origin? [y/N] y
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 703 bytes | 0 bytes/s, done.
Total 5 (delta 3), reused 0 (delta 0)
remote: 
remote: Create pull request for develop:
remote:   http://github.com/xxxxxxxxxxxx
remote: 
   7a0f2a1..19ff088  develop -> develop
Counting objects: 1, done.
Writing objects: 100% (1/1), 177 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
 * [new tag]         1.0.1 -> 1.0.1

```

sr-release asks the operator first if the updates in the CHANGELOG.md are finished:
```
Have you checked and updated CHANGELOG.md file? [y/N]
```
 Then it shows the lastest tag if any exists and asks for new one. 
 
```
 The lastest tag is: 1.0.0
 Enter the new tag and press [ENTER]
```
 Then the rest is automated.