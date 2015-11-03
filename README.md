# git ignoregenerator
ignoregenerator is a little bash script that extends git. The purpose of ignoregenerator is to generate content for .gitignore
by using github's gitignore repo.


## Install
Download git-ignoregenerator and put it in a folder that's included in your $PATH or make a new folder to put it in and include that path to you r $PATH.

**NOTE:** On first run it might be a bit slow because it will clone the gitignore repo.

## Usage

Say you are writing a Go application on Windows using VIM, and you want .gitignore to ignore files related to these things that don't need to be part of your repo. Make a .ignore_generator like this.

```
Go
Global/Windows
Global/Vim
```

**NOTE:** "Global/" is neede because the Windows and Vim gitignore files are in the Global folder of the gitignore repo.

Then use
`git ignoregenerator update`

Then it will add a section at the end of your .gitignore file that looks something like this:

```
##### GENERATED START #####

SomeFileToIgnore
[...]

##### GENERATED END #####
```

All it does is concatenating the files written in the .ignore_generator file and putting the content between those two comments. 

You can run the command again as you add or remove files from the .ignore_generator, or after having run `git ignoregenerator upgrade`, to do the apply any changes.

The ignoregenerator try to leave the rest of the file alone. That means, that you can add files you want to .gitignore file outside of those comments, and they should be safe.




### Update to newest gitignore repo
Run the following:
`git ignoregenerator upgrade`


## Possible issues

The gitignore files concatenated contain conflicting files.

Keeps re-adding new generated statements. If it does this, it's because it adds ##### GENERATED START ###### at the end of the line which contains a file name, makeing it unable to see that the generated section has started.


# Disclaimer
If you are using this, you are using this at your own risk. 