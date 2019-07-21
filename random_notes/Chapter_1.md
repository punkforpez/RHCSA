# Chapter One Summary:

- This is a basic intro chapter that describes the testing processes and differences between RHCSA and RHCE.  This book covers study material for both exams. The RHCSA exam is covered in Chapters 1-9. 

- Acquiring Red Hat Linux can be done so through a paid subscription to Red Hat or using a third-party rebuild (CentOS).  CentOS is functionally identical to RHEL without access to subscription management. 

- RHCSA requires the configuration of a physical machine as virtual 
  
  host. 

- Minimum partitioning scheme:
  
    /dev/sda1    /boot
  
    /dev/sda2    /
  
    /dev/sda3    swap 

- Deploy HTTP and FTP servers to practice with RHEL installs over 
  
  network (not required for exam but good to know)
  
    +Default services for FTP are vsFTP
  
    +Default services for HTTP are Apache web server (httpd)

- Use installation files from RHEL install DVD for transfer server content

#### ** Port 80 must be open in the firewall **

## Creating HTTP (Apache) Server Folder

##### 1. Mounting ISO file

cd to directory where file is located

    # sudo mount -o loop FILENAME.iso /directory/of/file

to unmount a loop

    # sudo umount -d FILENAME.iso

##### 2. Install and configure Apache Server

    # sudo yum -y install httpd
    # sudo systemctl start httpd
    # sudo systemctl enable httpd

##### 3. Create a subdirectory for your files (Apache files standard directory is /var/www/html)

    # sudo mkdir /var/www/html/inst

##### 4. Copy files from mounted DVD over to the HTML directory

    # sudo cp -a /media/. /var/www/html/inst/

##### 5. Ensure proper permissions are applied

    # sudo chcon -R --reference=/var/www/html /var/www/html/inst        

##### 6. Configure server to run and enable to start on boot

    # sudo firewall-cmd --permanent --add-service=http
    # sudo firewall-cmd --reloadk
    # sudo systemctl restart httpd
    # sudo systemctl enable httpd

##### 7. Verify the Apache Server is enabled and running properly

- in a web browser, navigate to 127.0.0.1/inst
- A page showing the server is running properly will display

## CREATING FTP Server

##### 1. Install vsFTP

    # sudo yum install vsftpd

##### 2. Enable vsFTP

    # sudo systemctl enable vsftpd

##### 3. To grant remote access

    # sudo firewall-cmd --permanent --add-service=ftp
    # sudo firewall-cmd --reload

##### 4. Enable FTP server

    # sudo systemctl enable vsftpd

##### 5. Navigate to FTP via web browser

    ftp://127.0.0.1/

##### 6. /pub directory shown in FTP server is located /var/ftp/pub
