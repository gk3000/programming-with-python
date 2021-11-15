# Terminal

## MacOS most used commands.

On MacOS to use a terminal you should just start Terminal app. 
To go to some folder:

    cd path_to_a_target_directory_(folder)

To go one level up in the folder hierarchy:

    cd ..

To see a list of folders and files in the current folder:

    ls

And to see them with hidden folders/files run

    ls -a
    
To create a new folder:

    mkdir name_of_a_new_folder

To create a new file in the current folder:

    touch filename


To remove a folder:

    rm -rf folder_name

To find and remove specific instances of folders inside current folder:

    rm -rf `find . -type d -name folder_name`

or

    find . -name NAMEOFFOLDERS -exec rm -rf {} \;

---

## Windows most used commands.

To start a terminal on Windows run cmd.exe.

To go to some folder:

    cd path_to_a_target_directory_(folder)

To go one level up in the folder hierarchy:

    cd ..

To see a list of folders and files in the current folder:

    ls

To create a new folder:

    mkdir name_of_a_new_folder

To create a new file in the current folder:

    echo $null >> filename
