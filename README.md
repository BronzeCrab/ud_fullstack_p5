## ud_fullstack_p5
### The IP address and SSH port so your server
#### IP
52.88.155.87
#### SSH PORT
2200
### Complete URL to application.
### A summary of software you installed and configuration changes made
#### What I've done:
1. added new user grader, created file `/etc/sudoers.d/grader` with necessary permissions. Like so: `adduser grader` File `/etc/sudoers.d/grader` has `grader ALL=(ALL) NOPASSWD:ALL` inside
2. `sudo apt-get update` - to retrive new package list
3. `sudo apt-get upgrade` - to update software, based on the list from previous command
4. Make changes in `/etc/ssh/sshd_config`, set `Port 2200` and `PasswordAuthentication no`
5. Configired ufw using `ufw`:

  ```{r tidy=FALSE}
sudo ufw status
ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 2200
sudo ufw allow www
sudo ufw allow ntp
ufw enable
```
6. Configure the local timezone to UTC: `dpkg-reconfigure tzdata`
7. Install (like [here][id1]) and configure Apache to serve a Python mod_wsgi application. Added `WSGIScriptAlias / /var/www/html/myapp.wsgi` to `/etc/apache2/sites-enabled/000-default.conf` near form ending of `</VirtualHost>` block.
8. 

### List of third-party resources
* https://www.digitalocean.com/community/tutorials/installing-mod_wsgi-on-ubuntu-12-04
* https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-14-04
* http://superuser.com
* http://markdowntutorial.com
* http://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt
[id1]: https://www.digitalocean.com/community/tutorials/installing-mod_wsgi-on-ubuntu-12-04
[id2]: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-14-04
