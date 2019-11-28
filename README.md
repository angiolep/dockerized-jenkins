# jenkins
TBD

```
# /etc/hosts

127.0.0.1   jenkins.local.net
127.0.0.1   jenkins-slave1.local.net
```


## slave first!

```sh
$ ./jenkins/slave/start 1
```

## then master 

```sh
./jenkins/master/start
```

### configuration

 * http://jenkins.local.net:18080/
 * `docker container exec jenkins-master cat /var/jenkins_master/secrets/initialAdminPassword`
 * Install plugins
    * (-) OWASP Markup Formatter
    * (+) SSH Agent
    * (+) Matrix Authorization Strategy
    * (-) Ant
    * (-) Gradle
    * (-) Subversion
    * (-) LDAP
    * (-) Email Extension
    * (-) Mailer
 * Create first admin user (e.g. your laptop $USER)
 
 * Manage Jenkins > Manage Users
     * Create user (git/login)   
     
 * Manage Jenkins > Configure Global Security
    * Matrix-based security 
    * Add user o group 
        * paolo, all possible rights
        * git, limited rights (overall:read, job:build, job:discover, job:read)
    * Do not Prevent Cross Site Request Forgery exploits
         
 * Jenkins > Credentials > (global)
    * Add Credentials
        * Kind: SSH Username with private key
        * cat ./jenkins/master/.ssh/id_rsa | pbcopy       
   
 * Jenkins > Manage Jenkins > Manage Nodes and Clouds
    * New Node
        * Name: slave1
        * Permanent Agent
        * Remote Root Dir: /home/jenkins
        * Launch method: Launch Agent via SSH  
        * Host: jenkins-slave1.local.net
        * Credentials: jenkins
                      