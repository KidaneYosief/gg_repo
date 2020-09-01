
 #################################################################################
 
                                    dealing with linux commands 
									
 #################################################################################

export branchName=`git rev-parse --abbrev-ref HEAD`

export commitid=`git rev-parse HEAD`

export build=${bamboo_buildNumber}

echo "
<!DOCTYPE html>
<html>
<head>
<title>Tcses-version</title>
</head>
<body>

 

<p>Build number is: ${build}</p>
<p>Branch name is: ${branchName}</p>
<p>Commit ID is: ${commitid}</p>

 

</body>
</html>
" > /tmp/output.txt

 
 find . -type d | wc -l
 export c=`find test1-* -type d | wc -l`
 
 

`find tdhs/ -name '*.war' -o -name '*.jar' -o -name '*.pom' -o -name '*.properties' -o -name '*.sha1' -type f -mtime +3 -exec rm -f {} \;`


 #################################################################################
 
                                    checking for number of processors
									
 #################################################################################
 
cat /proc/cpuinfo | grep processor | wc -l

top and press 1

 
 
 #################################################################################
 
                                    IN DEV
									
 #################################################################################

 

 ./lrsq /s:10.19.15.35 /p:6500 /que:drs3246  /dest:LRSQ4678 /form:STD /writer:DRS3246 /file:anyq0000.q    
 
 
 #################################################################################
 
                                    IN TEST
									
 #################################################################################
 
 
 ./lrsq /s:10.19.15.35 /p:6501 /que:drs4679  /dest:LRSQ4679 /form:STD /writer:DRS4679 /file:anyq0000.q
 
 
 
  git config --global core.autocrlf true


 
 #################################################################################
 
                            Installing maven in linux
							
 #################################################################################
 
 
 1. `sudo wget http://mirrors.ibiblio.org/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz –P /tmp`
	
	if you can download directly into linux, you can copy it from locat -- scp file user@servername:/tmp
	
 2. `sudo tar xf /tmp/apache-maven-3.6.3-bin.tar.gz –C /opt`  -- or 
 
		`tar -zxvf apache-maven-3.6.3-bin.tar.gz`
		`mv apache-maven-3.6.3 /opt/maven`
		`ln -s apache-maven-3.6.3 maven`
    
 3. `sudo vi /etc/profile.d/maven.sh` --- add --
 
        export M2_HOME=/opt/maven
        export MAVEN_HOME=/opt/maven
        export PATH=${M2_HOME}/bin:${PATH}
 4. sudo chmod 644 /etc/profile.d/maven.sh
 5. source /etc/profile.d/maven.sh
 
 
 #################################################################################
 
				Installing Ansible into Window Box
				
 #################################################################################
 
 1. install cigwin -- https://oznetnerd.com/2017/05/19/installing-ansible-windows/
 2. alias cyg-get="C:\Users\TN326BF\tools/setup-x86_64.exe -q -P"
 
		curl cygwin32-gcc-g++ gcc-core gcc-g++ git libffi-devel nano openssl openssl-devel python-crypto python2 python2-devel python2-openssl python2-pip python2-setuptools tree
 
		curl cygwin32-gcc-g++ tree
		
 #################################################################################
 
                    Installing Chrome into Linux
					
 #################################################################################
 
 1. Follow this link -  https://www.cyberciti.biz/faq/howto-install-google-chrome-on-redhat-rhel-fedora-centos-linux/
 
 if the wget is not able to download, 
 
 it can be done by downloading the rpm file locally and 
 
 scp the file into the respective server
  
  there is also anothe link you can look https://access.redhat.com/discussions/917293
  
 #################################################################################
 
                    fixing merge-conflict 
					
 #################################################################################
  
  git checkout --ours PATH/FILE  -- for ours/theirs


 #################################################################################
 
                   searching a file that has specific contents
				   
 #################################################################################
 
grep -iRl "https://tcses-dev.dhs.tn.gov/tcses" ./



 #################################################################################
 
                   If youwant to be root in a linux box 
				   
 #################################################################################

1. sudo vi
2. enter ":! sh" and hit enter


 #################################################################################
 
                   dealing with firewall, netstat and opening ports
				   
 #################################################################################
 
			firewall-cmd --list-all

			firewall-cmd --zone=public --permanent --add-port=8081/tcp

			firewall-cmd --reload

			netstat -atn
			lsof -i :8080
			sudo lsof -i -P -n | grep LISTEN

 #################################################################################
 
                   dealing with postgres
				   
 #################################################################################
 
sudo passwd postgres
Username to my postgres -----  postgres
Password to my postgres -----  postgres

psql -h localhost -U postgres -d postgres
psql -d dbamane -u dbUser

su - postgres
psql -U postgres
create user bitbucket_user;
alter user bitbucket_user with encrypted password 'bitbucket_user';
create database bitbucket_db;
GRANT ALL PRIVILEGES ON DATABASE bitbucket_db TO bitbucket_user;

drop user username

create user jira_user;
alter user jira_user with encrypted password 'jira_user';
create database jira_db;
GRANT ALL PRIVILEGES ON DATABASE jira_db TO jira_user; 


#################################################################################################################

								INSTALLING DOCKER IN LINUX

#################################################################################################################

1.  sudo yum -y update
2.  yum install -y docker
3.  service docker start/stop/restart/status
4.  docker info
5.  docker images
6.  docker ps -- docker process status
7.  docker ps -a
8.  docker pull jenkins:latest​
9.  docker container run --name jenkinscontainer –p 8080:8080 –p 50000:50000 jenkins:latest​
10. docker container stop/start/restart ContainerName or ContainerID​
11. docker container rm ContainerName or ContainerID​
12  docker image rm imageRepo or ImageID​




#################################################################################################################

							Installing git and java

#################################################################################################################

1. sudo yum groupinstall "Development Tools"
2. sudo yum install gettext-devel openssl-devel perl-CPAN perl-devel zlib-devel, 
3. sudo yum install zlib-devel   ( sometime this migh be enough instead of step 2)
3. tar -zxf git.tar.gz
4. cd git-*
5. make configure
6. ./configure --prefix=/usr/local
7. sudo make install


#################################################################################################################

			postgresQL install

#################################################################################################################


1. sudo chmod 777 postgresql-9.6.16-2-linux-x64.run
2. sudo ./postgresql-9.6.16-2-linux-x64.run
3. sudo systemctl enable postgresql-9.6
4. sudo systemctl status postgresql-9.6
5. export PATH=/opt/PostgreSQL/9.6/bin:$PATH to .bash_profile
6. psql -U postgres
7. create DB and like the following commands


	CREATE USER bitbucket_user;
	ALTER USER bitbucket_user WITH ENCRYPTED PASSWORD 'bitbucket_user';
	CREATE DATABASE bitbucket_db WITH ENCODING 'UNICODE' LC_COLLATE 'C' LC_CTYPE 'C' TEMPLATE template0;
	GRANT ALL PRIVILEGES ON DATABASE bitbucket_db TO bitbucket_user;
8. \q  ------which will take you out of the DB

update two/one files in postgres  and update them under root user
`# pg_hba.conf`
`# postgresql.conf -- this might not need to be updated`


#################################################################################################################

				INSTALLING Nexus IN LINUX 

#################################################################################################################

1. cd /opt && mkdir app
2. sudo wget -O nexus.tar.gz https://download.sonatype.com/nexus/3/latest-unix.tar.gz
3. sudo tar -xvf nexus.tar.gz
4. sudo mv nexus-3* nexus
5. sudo adduser nexus
6. sudo chown -R nexus:nexus nexus
7. sudo chown -R nexus:nexus sonatype-work
8. sudo vi  nexus/bin/nexus.rc
9. run_as_user="nexus"
10. sudo vi nexus/bin/nexus.vmoptions

`
-Xms2703m
-Xmx2703m
-XX:MaxDirectMemorySize=2703m
-XX:+UnlockDiagnosticVMOptions
-XX:+UnsyncloadClass
-XX:+LogVMOutput
-XX:LogFile=../sonatype-work/nexus3/log/jvm.log
-XX:-OmitStackTraceInFastThrow
-Djava.net.preferIPv4Stack=true
-Dkaraf.home=.
-Dkaraf.base=.
-Dkaraf.etc=etc/karaf
-Djava.util.logging.config.file=etc/karaf/java.util.logging.properties
-Dkaraf.data=/nexus/nexus-data
-Djava.io.tmpdir=../sonatype-work/nexus3/tmp
-Dkaraf.startLocalConsole=false 
`

11. sudo vi /etc/systemd/system/nexus.service

[Unit]
Description=nexus service
After=network.target

[Service]
Type=forking
LimitNOFILE=65536
User=nexus
Group=nexus
ExecStart=/app/nexus/bin/nexus start
ExecStop=/app/nexus/bin/nexus stop
User=nexus
Restart=on-abort

[Install]
WantedBy=multi-user.target

12. sudo chkconfig nexus on
13. sudo systemctl start nexus

#################################################################################################################

				INSTALLING JENKINS IN LINUX using YUM

#################################################################################################################

1. sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
2. sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
3. sudo yum install jenkins
4. service jenkins start
5. systemctl status jenkins
6. sudo systemctl enable jenkins

#################################################################################################################

			To upgrade jenkins to new version

#################################################################################################################

sudo yum update jenkins


#################################################################################################################

			to switch to the jenkins user when it did not have shell 

#################################################################################################################

						sudo su -s /bin/bash jenkins

#################################################################################################################

If you find a problem with something like "File contains no section headers."

please remove the jenkins.repo using

sudo rm /etc/yum.repos.d/jenkins.repo

to uninstall Jenkins -- 

sudo yum remove jenkins

#################################################################################################################

			Creating and deleting user in linux

#################################################################################################################

#useradd -m -s /bin/bash -c "comment" username_You_want -- create user

#passwd username_You_want -- give password

#userdel -r username_You_want -- deleting user

#usermod -aG wheel username_You_want -- giving user the root level access

# sudo username_You_want -- switching user

$ groups -- to check user of the configured username_You_want

$ sudo whoami -- to check if it has root level




#################################################################################################################

			Installing Eclipse in linux   - https://www.javahelps.com/2015/03/install-latest-eclipse-in-ubuntu.html

#################################################################################################################

1. download tar file of eclipse into window and ship it to linux -- https://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/2019-12/R/eclipse-jee-2019-12-R-linux-gtk-x86_64.tar.gz&mirror_id=1135
2. install xming in window ... https://sourceforge.net/projects/xming/
3. copy downloaded eclipse into linux and unzip the tar file
4. make sure display is exported .. Xvfb :1 -ac -screen 0 1024x768x8 & export DISPLAY=:1
5. update /etc/ssh/sshd_config and enable 
		X11Forwarding yes
		X11DisplayOffset 10
		X11UseLocalhost yes
6. restart the service 
		systemctl start sshd.service
		systemctl enable sshd.service
7. start eclips by running the ./eclpse executable file
8. Install and start xming 

#################################################################################################################

			Installing node in linux using yum

#################################################################################################################

1. curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash -
2. sudo yum install nodejs

#################################################################################################################

				Special commands in linux

#################################################################################################################

getent passwd username | cut -d: -f7

######################################################################

        Creating encrypted password in base64
		
######################################################################

echo -n 'myuser:mypassword' | openssl base64

 

######################################################################

    patching, prune, renaming branches and amending comments in git
	
######################################################################

1.  git remote prune origin
2.  git commit --amend -m "JiraID -"
3.  git branch -m newbranchName
4.  git diff origin/branch_TCSESMIG-TCSESMIG-TCSESBATJOB-17 master  -- diff between two branches
5.  git format-patch master --stdout > fix_empty_poster.patch  ## to create a patch 
6.  git format-patch master file/s--stdout > fix_empty_poster.patch  ## to create a patch for a specific file
7.  git apply --check < ../tcses-patches/tcses-online.patch  ## to check if the apply will work
8.  git apply --check -R < ../tcses-patches/tcses-online.patch  ## to check if the apply will work in reverse way
8.  git apply --stat fix_empty_poster.patch  ## to check what the changes will look like
9.  git am --signoff < fix_empty_poster.patch ## to apply patches if you like them
10. git apply -R ../tcses-patches/tcses-online.patch ## to apply patches if you like them in reverse way

 

######################################################################

        working with npm and ng
		
######################################################################

        npm install -g @angular/cli@latest
        ng update --all
        ng build --outputPath=~/workspace/tcses-online/src/main/resources/static

 
######################################################################

    Config server.xml in tomcat to deploy new and undeploy old one
	
######################################################################

			`<Host name="localhost"  appBase="webapps"`
            `unpackWARs="true" autoDeploy="true" undeployOldVersions="true">`
            
            

######################################################################

    Applying curl commands
	
######################################################################

curl -o filename url
opt/runtime/hs1cseproduction/src/main/java/gov/tn/tcses/actions/CieUpdateNoncoopGoodCause.java



######################################################################

    Checking all the available java in the system
	
######################################################################

`sudo update-alternatives --display java`

######################################################################

    Installing  Jar commands
	
######################################################################
		
`yum install -y java-devel`	


######################################################################

    pinging  Jar commands
	
######################################################################
		
`telnet ipaddress portnum`	



######################################################################

    finding file with pattern and delete them 
	
######################################################################
		
`find /var/log -name "*.log" -type f -mtime +30 -exec rm -f {} \;`


######################################################################

   finding all files under specific folder and delete them all files
	
######################################################################
		
`find /opt/backup -type f -mtime +30 -exec rm -f {} \;`

######################################################################

   Find and delete all the older folders keeping some numbers of the folder
	
######################################################################
		
`ls -dt kid* | tail -n +3 | xargs rm -rf`

		