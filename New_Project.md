#Starting a New Project

1. Create a new project directory in some standard location.  
 + For example, I put projects in D:\Documents\Repos
 + If my project is called "My Project", I would create a new empty folder "D:\Documents\Repos\MyProject"
 + Note removal of spaces from filenames; that prevents later headaches
 
2. Go to https://github.com and click the button to create a new project.
 + Give it the same name as the folder, in my case "MyProject"
 + Check the "Create README.md" option
 + Select an appropriate .gitignore file
 + Select an appripriate license.  I like the MIT license.
 
3. Using smartgit(the free version from http://www.syntevo.com/smartgit/), "Clone" the github.com project into the project directory.
 + Thus, I would select Github.com, then find the MyProject github project, and on a later screen, set the destination folder to "D:\Documents\Repos\MyProject".
 
4. Now, edit the .gitignore if necessary.
 + I often use the github project called "github/gitignore" containing many sample files.  Copy and paste from as many as needed into your project's .gitignore file.
 
5. Edit the README.md file to describe the project in moderate detail.

6. Now, using the tool of your choice (an IDE, the Unity game engine editor, the Unreal game engine editor, or whatever), create a new project and put it into the directory just created.
 + For many IDEs, if you create a project MyProject, it will end up in D:\Documents\Repos\MyProject\MyProject.  
 + If that happens, you might be able to get away with first closing the IDE/editor/whatever and then moving the files from 
 D:\Documents\Repos\MyProject\MyProject to D:\Documents\Repos\MyProject and then deleting the now-empty 
 D:\Documents\Repos\MyProject\MyProject folder.
 + Be ready to redo the "create new project" step if that doesn't work.
 
7. Test that all is good by closing and re-opening the IDE/editor/whatever and reloading the project.

8. Close all IDEs/Editors/etc. that might be using any files in the D:\Documents\Repos\MyProject directory.
 + Not doing so can prevent committing and pushing the repository to github.com

9.  Use smartgit to stage, commit, and push the files (except those automatically ignored by the .gitignore file) to github.com

10. Go to github.com and find the project and make sure all is ok.

11.  What if you did it in the wrong order? You already have a project and want to put it on github?  There are many solutions.  One that is reasonably robust is the following.
 1. Back up the project directory somewhere.
 2. Create a new empty directory "D:\Documents\Repos\MyProject"
 3. Do steps 2, 3, 4, and 5 above to make it a github repository
 4. Ensure the IDE/Editor/etc. is not running
 5. Copy all the files from the original project directory into "D:\Documents\Repos\MyProject"
 6. Open editor/IDE/etc. to make sure it works.
 7. If all is ok, do steps 8, 9, and 10.
