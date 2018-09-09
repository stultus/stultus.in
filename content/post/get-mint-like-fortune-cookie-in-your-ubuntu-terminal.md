+++
date = "2010-11-03T09:32:45-04:00"
draft = false
highlight = true
title = "Get Mint Like Fortune-Cookie in your Ubuntu Terminal!"
tags = ["hack", "linux mint", "terminal"]
+++

Most of you might have noticed a cool feature which is available in Linux-Mint,
each time when you open a Terminal, it will display a cool - simple quote.
We don't have this option in Ubuntu. but we can have it. 
First we have to install the Fortune Cookie Database in our system. we can do that by typing the following in a terminal. 

```
sudo apt-get install fortune-mod cowsay 

sudo apt-get install fortune
```
Now we have the database installed in our system. have a try by typing the following: 

```
fortune
```

Now let us borrow a cool script from the Mint people.
open  your favorite editor and type the following script in it and save it in `/usr/bin/` by the name `fortune`.

```
#!/bin/bash
RANGE=4
number=$RANDOM
let "number %= $RANGE"
case $number in
 0)
  cow="small"
  ;;
 1)
  cow="tux"
  ;;
 2)
  cow="koala"
  ;;
 3)
  cow="moose"
  ;;
esac

RANGE=2
number=$RANDOM
let "number %= $RANGE"
case $number in
 0)
  command="/usr/games/cowsay"
  ;;
 1)
  command="/usr/games/cowthink"
  ;;
esac

/usr/games/fortune | $command -f $cow
```

 Now change the mode of this file to executable by typing the following in the terminal

 ```
     sudo chmod +x /usr/bin/fortune
 ``` 
  finally call this script from `.bashrc` file.

  ```
    sudo echo "/usr/bin/fortune" >> ~/.bashrc
```

Done !!! Now you will get a cool Fortune-Cookie , each time when you open the terminal...

Enjoy !! and Happy Hacking !! 