# **STEP 5: Setting an SSH key**

Consistently logging into your course-specific account onto `ieng6` takes a lot of time, especially typing in your password every time.

To automate this process a little, you can use `ssh` keys.

**Try the following:**
1. Type `ssh-keygen` in your terminal.
2. The terminal will then ask you a series of questions such as passphrase.
3. Press `enter` three times (or you can make a passphrase but make sure to remember it!).
   Your output will look something like this:
   ```
   PS C:\Users\Francisco\Documents\GitHub\cse15l-lab-reports> ssh-keygen
   Generating public/private rsa key pair.
   Enter file in which to save the key (C:\Users\Francisco/.ssh/id_rsa): 
   C:\Users\Francisco/.ssh/id_rsa already exists.
   Overwrite (y/n)? y
   Enter passphrase (empty for no passphrase): 
   Enter same passphrase again: 
   Your identification has been saved in C:\Users\Francisco/.ssh/id_rsa.
   Your public key has been saved in C:\Users\Francisco/.ssh/id_rsa.pub.
   The key fingerprint is:
   SHA256:8HUcJGvtSo5yoT8lIepsJZupofoSwju2hX1R7fPQfJQ francisco@DESKTOP-ES7A2CB
   The key's randomart image is:
   +---[RSA 3072]----+
   |        .  = ..  |
   |      .. .+ +E   |
   |      oooooo.    |
   |.    o .S=.o..   |
   |o.o o o..==..    |
   |.oo= Bo ooo.     |
   |.=..O  +.        |
   |=+=o    ..       |
   +----[SHA256]-----+
   ```
   
   **NOTE: Your output may differ slightly by note having the `Overwrite (y/n)?`. I simply got this question because I have already done this process. If you have done this        process before, you will have the same question as I recieved.**
   
4. Then type `ssh-add 'C:\Users\Francisco\.ssh\id_rsa'` into your terminal (only difference is the username after `Users/`).
5. If you recieve an output stating the directory does not exist, open your serach menu on your laptop, and search for `services`.
6. Once in `services`, scroll down to `OpenSSH Server`. Click on it, and change the status to `Manual`.
7. Now open the search bar once more, and find `Windows PowerShell`. Open this and click on `run as Administrator`.
8. Then a PowerShell terminal will open up. Type in these commands one-by-one:
   * `Get-Service ssh-agent | Set-Service -StartupType Manual`
   * `Start-Service ssh-agent`
   * `Get-Service ssh-agent`
   * `ssh-add 'C:\Users\Francisco\.ssh\id_rsa'`, but instead of `Francisco`, input the username of the laptop from which you're currently logged in as.
   
9. You should get an output in the PowerShell stating that the "identity" was added to your desktop.
10. Now to ensure this is correct, go back to VSCode and type `ssh-add 'C:\Users\Francisco\.ssh\id_rsa'` into the terminal (you should get the same output as the previous step).
11. Now type `ssh cs15lwi22agc@ieng6.ucsd.edu` into the terminal and your password once more.
12. Enter `mkdir .ssh` into the terminal.
13. Logout using `exit`.
14. Now enter `scp /Users/Francisco/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys`, with `Francisco` being replaced with your username.
15. If you followed these steps correctly, the terminal should no longer ask for your password whenever you use the `ssh` or `scp` commands.

Below is an image of changing the `OpenSSH Server` to `Manual`.
![Image]()

Below is an image of how the terminal should respond by no longer requiring your password whenever using the `ssh` or `scp` commands.
![Image]()
