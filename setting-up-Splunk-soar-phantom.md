#Setting up Splunk SOAR Phantom

## Step1: Update the System
```
sudo yum clean all
```
```
sudo yum update
```
## Step2: Download the Phatom package
```
wget -O splunk_soar-unpriv-6.2.1.305-7c40b403-el7-x86_64.tgz "https://download.splunk.com/products/splunk_soar-unpriv/releases/6.2.1/linux/splunk_soar-unpriv-6.2.1.305-7c40b403-el7-x86_64.tgz"
```

## Step3:Extract the package
```
tar -xzvf ./splunk_soar-unpriv-<version>.tgz -C /opt/phantom
```

## Step4:Prepare the system for the unprivileged installation
```
./soar-prepare-system 
```
- `Install pre-requisite RPM packages required by Splunk SOAR (Y/n)`: If prompted, you must answer Y to proceed.
- `GlusterFS is only needed if you are using an external file share. This is common if you're constructing a Splunk SOAR cluster. Do you want to run this step? (Y/n):` You only need to answer Y if you are setting up certain cluster - - 
- `configurations of Splunk SOAR (On-premises)`, but you can answer Y even on individual instances.
- `Enable the ntpd service to guarantee clock synchronization. Do you want to run this step? (Y/n)`: Answer Y.
- `Create a non-privileged user for running Splunk SOAR (On-premises). (Y/n):` If prompted, you must answer Y to proceed.
- `Do you want to set a password for <non-privileged_user> now? (Y/n):` Answer Y if you created a non-privileged user for running Splunk SOAR (On-premises) in the previous step.
- `Set system resource limits for Splunk SOAR user, particularly file descriptor limits, which are low by default. (Y/n):` Answer Y.

## Step4:Install Splunk SOAR
```
./soar-install
```

## Step5:Access the GUI
If you installed Splunk SOAR (On-premises) as an unprivileged user, log in to Splunk SOAR (On-premises)'s web interface at the custom HTTPS port.
```
https://<ip address or hostname>:<your https port>
```
Log in using the default credentials. Use `soar_local_admin` as the username and password as the `password`. 
