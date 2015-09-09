## ud_fullstack_p5
### The IP address and SSH port so your server
#### IP
52.88.155.87
#### SSH PORT
2200
### Complete URL to application

This is a normal paragraph:
    asgasgasga
### A summary of software you installed and configuration changes made
#### What I've done:
1. added new user grader, created file /etc/sudoers.d/grader with necessary permissions
2. `sudo apt-get update` - to retrive new package list
3. `sudo apt-get upgrade` - to update software, based on the list from previous command
4. Make changes in `/etc/ssh/sshd_config` - set `Port 2200` and `PasswordAuthentication no`
5. Configired ufw using `ufw`:
6.sudo ufw status
  ufw default deny incoming<br>
  sudo ufw default allow outgoing<br>
  sudo ufw allow 2200<br>
  sudo ufw status<br>
  sudo ufw allow www<br>
  sudo ufw allow ntp<br>


  afaa
  
* finger
* apache2
* postgresql
* 

### List of third-party resources
* https://www.digitalocean.com/
* http://superuser.com
* http://markdowntutorial.com
* http://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt
