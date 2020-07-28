# [Build Anaconda Environment on Linux](https://problemsolvingwithpython.com/01-Orientation/01.05-Installing-Anaconda-on-Linux/) 

## 1. Visit the Anaconda downloads page
Go to the following link: [Anaconda.com/downloads](https://www.anaconda.com/download/)

## 2. Get the link of latest version of Anaconda on Linux
Like this: [Anaconda3-2020.07-Linux-x86_64.sh](https://repo.anaconda.com/archive/Anaconda3-2020.07-Linux-x86_64.sh)

## 3. Use `wget` to download the bash installer
```sh
$ wget https://repo.anaconda.com/archive/Anaconda3-2020.07-Linux-x86_64.sh
```

## 4. Run the bash script to install Anaconda3
```sh
$ bash Anaconda3-2020.07-Linux-x86_64.sh
```
Accept the Licence Agreement and allow Anaconda to be added to your `PATH`. By adding Anaconda to your `PATH`, the Anaconda distribution of Python will be called when you type `$ python` in a terminal.

## 5. `source` the `.bash-rc` file to add Anaconda to your `PATH`
Now that Anaconda3 is installed and Anaconda3 is added to our `PATH`, `source` the `.bashrc` file to load the new `PATH` environment variable into the current terminal session. Note the `.bashrc` file is in the home directory. 
```sh
$ cd ~
$ source .bashrc
```

## 6. Result
```sh
(base) local_host:~ username $ 
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNjA2MzY0MDUsMjA1NTA2NzY4MV19
-->