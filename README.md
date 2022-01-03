# About this Repo

This repository contains two different sample yaml template to deploy Sonarqube to Openshift 4. This is not an ephemeral deployment since we are using Openshift PersistentVolume to mount data, logs and Sonarqube extensions, preventing data loss whenever Pod is being restarted. 

One template (`sonarqube-h2-db-template.yml`) is using H2 in-memory Database recommended for a non-production environment, while the other (`sonarqube-pgsql-db-template.yml`) is using a postgresql database which is more suitable for production usage. 

How To
--------------------------

Deploy template to Openshift, and creating a new application based on it. For Sonarqube with in-memory DB, 
```
$ oc create -f sonarqube-h2-db-template.yml

$ oc new-app --template sonarqube-h2-db
```

For Sonarqube with Postgresql database,
```
$ oc create -f sonarqube-pgsql-db-template.yml

$ oc new-app --template sonarqube-pgsql-db
```

Run maven command to check your code against Sonarqube
```
$ mvn clean verify sonar:sonar -Dsonar.projectKey=my-project -Dsonar.host.url=http://openshift-url -Dsonar.login=sonar-token
```

Versions
------------
- Openshift 4.9.6
- Sonarqube Community Edition Version 9.2.4 (build 50792)
- Postgresql 12


Blog Post
------------
```
https://edwin.baculsoft.com/2022/01/deploying-sonarqube-to-openshift-4-by-using-openshift-template/
```


Disclaimer
------------

```
This data is provided "as is" without any guarantee whatsoever. 
Feel free to fork, tinker, add, remove, change, or do whatever you want to it. 
```