**Installing WSL (Windows Subsystem for Linux) Ubuntu**

1. You need to enable WSL in Windows 10. Press the Windows key and type (to search) for `Turn Windows features on or off`. Open the selected option (see image 1 below)
1. Scroll down and check the box near Windows Subsystem for Linux. Press ok. You might need to restart you computer – if it asks, you do need to ☹. (see image 2 below)
1. (after restarting if necessary) Open the Microsoft store. Search for Ubuntu. Choose the result called &#39;Ubuntu&#39; published by Canonical Group Limited, and install it. Here's a link: [https://www.microsoft.com/store/productId/9NBLGGH4MSV6](https://www.microsoft.com/store/productId/9NBLGGH4MSV6)
2. If the store asks you to log in, but you don't want to, just say no. The program will install anyway.
3. Once it's installed, open Ubuntu from the start menu (you might want to type to search for it). You will need to wait a few seconds whilst it finishes installing. Then you will need to give a username (preferably all lower-case, must be just one word) and a password. Note: when you type the password, characters will not appear! Just type then press enter when you&#39;re done.
4. You're finished! You can play with the terminal now. 

**A quick intro to bash**

Some tutorials for learning bash 'properly' are listed in the ['work from home' document](https://gist.github.com/martinp23/2d9f00ee0f1e9e2a510efdb35a9b6292). Below is a quick intro.

5. Type `ls` to list items in the present directory
6. Find what the current directory path is: `pwd`   (means: print working directory)
7. Let&#39;s make a new directory called &#39;test&#39;: type `mkdir test`
8. Move into that new directory `cd test`
9. See if there&#39;s anything in here: `ls`
10. See if there&#39;s anything in the directory above: `ls ..`    (note: `..` means the directory above)
11. Learn what the ~ symbol does; type: `ls ~` (`~` refers to the home directory)
12. Let&#39;s make an empty file in our new directory: `touch testfile`
13. See if we can see it: `ls`
14. See more details: `ls -l`
15. Go back home (either `cd ~`   or `cd ..`)
16. Delete the directory you just made: `rm test` **It doesn&#39;t work!**
17. It didn&#39;t work because you had a file in there. Either: `rm test/testfile` then `rm test` or `rm -r test`  (-r = recursive)
18. A few notes: filenames with a &#39;.&#39; at the beginning are hidden. You can see them with `ls -a` or `ls -la`. Try this now in your home directory.
19. One of these files is `.bashrc`. This contains useful lines of code which run when you start a new shell and you will put more code into here when you install xtb.
20. The symbol \* matches anything. So in our earlier examples, `ls t\*`  would return &#39;test&#39;. `rm \*` deletes everything. Don&#39;t run it!
21. If you press &#39;tab&#39; while typing a command, often bash will show you all the possibilities. E.g. if you type `cd /` then hit tab, it will show you every possible subdirectory of / (which refers to the root directory: think &#39;my computer&#39; in Windows).
22. You can access WSL using a better terminal emulator in the form of Mobaxterm ([https://mobaxterm.mobatek.net/](https://mobaxterm.mobatek.net/)). Get the free version, install it. Press &#39;Session&#39; in the top left, then &#39;WSL&#39; in the top right of the resulting Window. This &#39;server&#39; will now be saved, and you can connect to it by double-clicking on the relevant icon on the sessions panel on the left of Mobaxterm. The advantage of using mobaxterm is that it has more features than the Windows terminal emulator.

**Updating the system**

Now that we&#39;ve worked out the basics of the terminal, let&#39;s quickly update the system with these commands:

- `sudo apt update`      (`sudo`: run as root (may prompt for password); `apt`: package-manager; `update`: update your list of packages/software)
- `sudo apt upgrade`     (actually upgrade those packages which need it)
- `sudo apt install vim nano`    (make sure important packages are installed)

Now we should quickly learn how to edit text. This can be crazy complicated to start with. There are two main editors to consider: `nano` and `vim`. The former is easier, the latter is more powerful.

* nano quick intro: [https://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/](https://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/)

* vim quick intro: [https://gist.github.com/jpalala/01a0785e9ff7051aa3c78a75564a68c9](https://gist.github.com/jpalala/01a0785e9ff7051aa3c78a75564a68c9) or [https://www.openvim.com/](https://www.openvim.com/)

Choose one and play around with it.

Finally, if you want to access files you create in wsl in Windows, you can type the following into a Windows explorer path: [\\wsl$\Ubuntu](./../../%5C%5Cwsl%24%5CUbuntu) .

You can access your Windows files from wsl/ubuntu by going to the /mnt directory (`cd /mnt`). Note: you might have file-system issues if you try to edit stuff directly on Windows drives from within WSL (so don't: keep stuff in your WSL /home/username directory).
