# OpenShift-Container-Platform-Workshop

http://labs.apps.ocp.cloudvillage.in/#/workshop/ocptigerteam/module/0-setting-up-client-tools


## Setting up client tools

https://github.com/openshift/origin/blob/master/docs/cluster_up_down.md#windows-with-docker-for-windows
`choco install openshift-cli`

## Step 1.

```
oc cluster up

Starting OpenShift using openshift/origin:v3.7.0 ...
Pulling image openshift/origin:v3.7.0
Pulled 1/4 layers, 28% complete
Pulled 2/4 layers, 74% complete
Pulled 3/4 layers, 78% complete
Pulled 4/4 layers, 100% complete
Extracting
Image pull complete
OpenShift server started.

The server is accessible via web console at:
    https://10.0.75.2:8443

You are logged in as:
    User:     developer
    Password: <any value>

To login as administrator:
    oc login -u system:admin
```

```
λ oc login -u system:admin
Logged into "https://10.0.75.2:8443" as "system:admin" using existing credentials.

You have access to the following projects and can switch between them with 'oc project <projectname>':

    default
    kube-public
    kube-system
  * myproject
    openshift
    openshift-infra
    openshift-node

Using project "myproject".
```


## Step 2.
```sh
# Login as developer to scope
oc login -u developer

oc get projects
oc new-project mycliproject-developer --description="My CLI Project" --display-name="CLI Project"
oc new-app redhatworkshops/welcome-php --name=welcome

oc get pods
oc get services
oc expose service welcome --name=welcome 
oc get routes

oc delete all --all
```

## Step 3.
```sh
oc project mycliproject-developer

oc expose service time
oc get routes
```

## Step 5.
```sh
oc new-project myjbossapp-developer --display-name="My JBoss Applications" --description="A place for my JBoss EAP Applications"
oc new-app --template=eap6-basic-sti -p APPLICATION_NAME=ks -p GIT_URI=https://github.com/RedHatWorkshops/kitchensink -p GIT_REF="" -p GIT_CONTEXT_DIR=""
```

**Note:** This wouldnt work locally, since not Redhat enterprise

## Step 6.
```sh
mysql -h localhost -P 3306 -u mysqluser -p supersecret
```

For PHP app, settings are not correct, use instead:
- username
- password
- database_name

## Step 8.
```sh
oc new-project binarydeploy-developer


```

https://blog.openshift.com/announcing-net-core-2-0-support-openshift/