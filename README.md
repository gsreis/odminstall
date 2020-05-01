# Installing Cloud Pak for Automation 20.0.1 on Red Hat OpenShift

- [Step 1: Create a namespace and get access to the container images](install.md#step-1-create-a-namespace-and-get-access-to-the-container-images)
- [Step 2: Prepare your environment for automation software](install.md#step-2-prepare-your-environment-for-automation-software)
- [Step 3: Create a shared PV and add the JDBC drivers](install.md#step-3-create-a-shared-pv-and-add-the-jdbc-drivers)
- [Step 4: Deploy the operator manifest files to your cluster](install.md#step-4-deploy-the-operator-manifest-files-to-your-cluster)
- [Step 5: Configure the software that you want to install](install.md#step-5-configure-the-software-that-you-want-to-install)
- [Step 6: Apply the custom resource](install.md#step-6-apply-the-custom-resource)
- [Step 7: Verify that the automation containers are running](install.md#step-7-verify-that-the-automation-containers-are-running)
- [Step 8: Complete some post-installation steps](install.md#step-8-complete-some-post-installation-steps)

##  Step 1: Create a namespace and get access to the container images

From your local machine, you can access the container images in the IBM Docker registry with your IBMid (Option 1), or you can use the downloaded archives from IBM Passport Advantage (PPA) (Option 2).

1. Log in to your cluster.
   ```bash
   $ oc login https://<CLUSTERIP>:8443 -u <ADMINISTRATOR>
   ```
2. Create an OpenShift project (namespace) in which you want to install the operator.
   ```bash
   $ oc new-project my-project
   ```
3. Add privileges to the project.
   ```bash
   $ oc adm policy add-scc-to-user privileged -z my-project
   ```
4. Download or clone the repository on your local machine and change to `cert-kubernetes` directory
   ```bash
   $ git clone git@github.com:icp4a/cert-kubernetes.git
   $ cd cert-kubernetes
   ```
   You will find there the scripts and kubernetes descriptors that are necessary to install Cloud Pak for Automation.
