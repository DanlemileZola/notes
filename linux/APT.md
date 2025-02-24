I want to make more in depth note about APT but first an important point about packages priority i learned today :

We can use /etc/preferences.d/ (being on Debian testing, i need to check if /etc/apt/preferences is still up to date) to set the rules about versions priority. 
But it only deals with versions, not instances. Meaning that if there is the same version of a package in two different releases (testing and unstable), even if unstable have higher priority, it wouldn't rules out the testing source. 
In that case, it's the order in the sources.list (or debian.sources for the future stable) that would decide which sources would be selected first. 

Despite using '# apt install -t unstable \<package>'. But on that, maybe i was too tired and didn't realized that it was indeed downloaded from unstable. I will retry before writing the rest of that part. 

I'm quite mad about myself, because i was looking into debian wiki about how APTSourcesList works and they talked a bit about priority but the answer was quickly found into the beginning of apt_preferences manpage. I lost almost 2 hours  in test and read time to understand why my configurations didn't worked before reading the right doc. A valuable lesson for the future : once understood what to look for, go RTFM !!! 

