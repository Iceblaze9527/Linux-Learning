# [Basic Vim Operation on Linux](https://www.runoob.com/linux/linux-vim.html)

## vi/vim 的基本使用

基本上 vi/vim 共分为三种模式，分别是
* **命令模式（Command mode）**
* **输入模式（Insert mode）**
* **底线命令模式（Last line mode）**

### 命令模式
用户在启动 vi/vim时默认进入命令模式。此状态下敲击键盘动作会被Vim识别为命令，而非输入字符。

以下是常用的几个命令：
-   `i` 切换到输入模式，以输入字符。
-   `x` 删除当前光标所在处的字符。
-   `:` 切换到底线命令模式，以在最底一行输入命令。

命令模式只有一些最基本的命令，因此仍要依靠底线命令模式输入更多命令。

### 输入模式
在命令模式下按下`i`就进入了输入模式。

按`ESC`键可随时退出输入模式。

### 底线命令模式
在命令模式下按下`:`就进入了底线命令模式。底线命令模式可以输入单个或多个字符的命令，可用的命令非常多。

基本的命令有：
-   `:q` 退出程序
-   `:w` 保存文件

按`ESC`键可随时退出底线命令模式。


### 4. Vim Search Patterns
To search for an expression just type the / key and then your search result while you are in a vim session. Once you hit enter, you can press "n" to go forward or "N" to go backward in your search results.
```sh
My pretty file is very pretty.

/pretty

will find the pretty words in the text file.
```

The ? search command will search the text file backwards, so in the previous example, the last pretty would come up first.  

```sh
My pretty file is very pretty.

?pretty

will find the pretty words in the text file.
```

### 5. Vim Navigation
Now you may notice, the mouse is nowhere is use here. To navigate a text document in vim, use the following keys:

-   h or the left arrow - will move you left one character
-   k or the up arrow - will move you up one line
-   j or the down arrow - will move you down one line
-   l or the right arrow - will move you right one character

### 6. Vim Appending Text
Now you may have noticed if you tried to type something you wouldn't be able to. That's because you are in command mode. This can get pretty confusing especially if you just want to open a file and enter text. The command mode is used for when you enter commands like h,j,k.l etc. To insert text you'll need to enter insert mode first.

-   i - insert text before the cursor
-   O - insert text on the previous line
-   o - insert text on the next line
-   a - append text after the cursor
-   A - append text at the end of the line

Notice how when you type any of these insertion modes, you'll see that vim has entered insert mode at the bottom of the shell. To exit insert mode and go back to command mode, just hit the Esc key.

### 7. Vim Editing

Now that we have a couple of lines written, let's edit it a bit more and remove some cruft.

-   x - used to cut the selected text also used for deleting characters
-   dd - used to delete the current line
-   y - yank or copy whatever is selected
-   yy - yank or copy the current line
-   p - paste the copied text before the cursor

### 8. Vim Saving and Exiting
Now that you've done your editing it's time to actually save and quit out of vim:

-   :w - writes or saves the file
-   :q - quit out of vim
-   :wq - write and then quit
-   :q! - quit out of vim without saving the file
-   ZZ - equivalent of :wq, but one character faster

-   u - undo your last action
-   Ctrl-r - redo your last action

You may not think ZZ is necessary, but you'll eventually see that your fingers may tend to lean towards this rather than :wq.

Whew that was a lot of information to take about Vim. Now that you know some basic commands and navigation, you can start editing some text files. There are many more options you can use in vim to increase your ability to master this text editor, head on to Vim's online guide to take a look.
<!--stackedit_data:
eyJoaXN0b3J5IjpbODEyMDgyOTA3XX0=
-->