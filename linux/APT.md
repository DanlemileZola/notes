I want to make more in depth note about APT but first an important point about packages priority i learned today :

We can use /etc/preferences.d/ (being on Debian testing, i need to check if /etc/apt/preferences is still up to date) to set the rules about versions priority. 
But it only deals with versions, not instances. Meaning that if there is the same version of a package in two different releases (testing and unstable), even if unstable have higher priority, it wouldn't rules out the testing source. 
In that case, it's the order in the sources.list (or debian.sources for the future stable) that would decide which sources would be selected first. 

Despite using '# apt install -t unstable \<package>'. But on that, maybe i was too tired and didn't realised that it was indeed downloaded from unstable. I wil retry before writing the rest of that part. 