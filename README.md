## Running Shell Script in Android

This Project/Repo is creating as guide on how to run a shell script in an Android Device

<p align="center">
    <img src=/screenshot.png alt="Running Script in Android">
</p>

### Prerequisites:

1. Having a rooted device helps, but I don’t think it is necessary.
2. Android Debug Bridge installed on your computer.
3. USB cable to connect the Android device to your computer (I use a MacBook Pro)

### Steps:

1. Connect Android phone to computer with USB cable.
2. Open new Terminal window on your computer.
3. Run “adb shell” command on the Terminal.
4. Run “ls” next.

Here’s what step 3 and 4 outputs should look like —

<p align="center">
    <img src=https://miro.medium.com/max/720/1*3ryjrgP2e3d4HBBSmLEnkw.png alt="Running Script in Android">
</p>

5. Run “cd data/local/tmp” next.
6. If you’re doing this for the first time, this directory is probably empty and doing an “ls” may not show anything. Also, “ls” at /data/ or at /data/local/ will probably give you permission denied, but go all the way in till data/local/tmp and you should be fine.
7. Now open any text editor and create a new file with the first line as -
#!/bin/sh
> I saved my shell script file as “get_process_info.sh”. 
If you want to name your’s something else that’s no problem but then change the filename in the step number 10. “ps -e” is the command that lists out all running processes on a Linux based device, so here’s what my script file looks like -
8. Now leave the current terminal window as it is and open another fresh new Terminal window.
9. Run “cd Desktop” on this new terminal. (or whichever path you saved your script file in).
10. Next run “adb push get_process_info.sh /data/local/tmp” (replace ‘get_process_info.sh’ with your file’s name from step 7)
This step should push your script file into the location /data/local/tmp.
11. Go back to the previous Terminal window that we left open in step 8.
12. Run “ls” command. You should see your file listed in its output-
<p align="center">
    <img src=https://miro.medium.com/max/720/1*FhZTZpqCtAnd1uu3_6kSQQ.png alt="Running Script in Android">
</p>
13. In this terminal itself, run “chmod 777 get_process_info.sh” next. (obviously replace filename with your’s). 

This step basically changes the read/write permissions of your shell script file to root user i.e. allows my script to fetch metadata of all system level processes as well. You may skip this step if root access is not needed for your script’s application in particular.
14. You may run “ls -l” to verify that the read/write permission did in fact get updated to root. It would look something like the image after step 15. (see highlighted in blue)
15. Next run the shell script file to verify if it yields the desired result. “./get_process_info.sh”. Here’s what the result would be -
<p align="center">
    <img src=https://miro.medium.com/max/720/1*wuhlVVK39Up_esoR90C1Zg.png alt="Running Script in Android">
</p>

### With Help from:
> https://utkarshopalkar.medium.com/how-to-run-shell-scripts-on-the-android-os-shell-from-within-your-java-react-native-android-app-72455e78948b
