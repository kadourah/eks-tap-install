
 1.  Install [TAP On EKS](
https://aws.amazon.com/quickstart/architecture/vmware-tanzu-application-platform/) using quick start:
        * Make sure to fill the CIDR
 2. Choose "Deploy into a new VPC."
 3. Fill required parameters
      * Make sure to save the key pair used as this will be used to connect RDP to windwos
 4. Make sure to fill **Remote access CIDR** , you can fill ```0.0.0.0/0```
 5. Review the **Outputs** in *CloudFormation* you should see a property named ```TAPGuiUrl``` which holds the URL of TAP.  This URL can be accessed from the Windows Bastion Machine
 6. Once configured you can use the Windows or Linux Bastion machine to connect
 7. Deploy [.NET Workload](https://github.com/sample-accelerators/steeltoe-weatherforecast) a workload : 
      * ```tanzu apps workload apply -f config/workload.yaml --label apps.tanzu.vmware.com/has-tests=true --type web --yes```
 8. Edit the pipeline to skip the maven testing as part of a supply chain , this was done by running the following command : ```kubectl edit pipeline developer-defined-tekton-pipeline -n tap-workload```
 9. Add repo as mentioned above to EKS:
    * <cloudformation id>/tap-supply-chain/tanzu-java-web-app-workload-tap-workload
    * <cloudformation id>/tap-supply-chain/tanzu-java-web-app-workload-tap-workload-bundle 