# About this Repo

This repository contains yaml template to deploy Sonarqube to Openshift. This is not an ephemeral deployment since we are using Openshift PersistentVolume to mount data, logs and Sonarqube extensions, preventing data loss whenever Pod is being restarted. 

This deployment method should not be used for production since still using H2 in-Memory Database.

How To
--------------------------

Deploy template to Openshift
```
oc create -f sonarqube-h2-db-template.yml
```

Run maven command to check your code against Sonarqube
```
mvn clean verify sonar:sonar -Dsonar.projectKey=my-project -Dsonar.host.url=http://openshift-url -Dsonar.login=sonar-token
```

Versions
------------
- Openshift 4.9.6
- Sonarqube Community Edition Version 9.2.4 (build 50792)


Disclaimer
------------

```
This data is provided "as is" without any guarantee whatsoever. 
Feel free to fork, tinker, add, remove, change, or do whatever you want to it. 
```