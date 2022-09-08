
 1.  Install [TAP On EKS](
https://aws.amazon.com/quickstart/architecture/vmware-tanzu-application-platform/) using quick start:
        * Make sure to fill the CIDR
 2. Choose "Deploy into a new VPC."
 3. Fill required parameters
      * Make sure to save the key pair used as this will be used to connect RDP to windwos
 4. Make sure to fill **Remote access CIDR** , you can fill ```0.0.0.0/0```
 5. Review the **Outputs** in *CloudFormation* you should see a property named ```TAPGuiUrl``` which holds the URL of TAP.  This URL can be accessed from the Windows Bastion Machine
 6. Once configured you can use the Windows for TAP UI.
 7. SSH to Linux Bastion machine:  ssh -i artifacts/`key` ubuntu@(`publicip`)
 8. SSH to Linux Bastion machine for app deployment
 9. download sample accelerator ```git clone https://github.com/sample-accelerators/steeltoe-weatherforecast```
 10. Deploy [.NET Workload](https://github.com/sample-accelerators/steeltoe-weatherforecast) a workload :   ```tanzu apps workload apply -f config/workload.yaml --label apps.tanzu.vmware.com/has-tests=true --type web --yes -n tap-workload```
 11.  Edit the pipeline to skip the maven testing as part of a supply chain , this was done by running the following command : ```kubectl edit pipeline developer-defined-tekton-pipeline -n tap-workload```
 12.  Add repo as mentioned above to EKS:
    * <cloudformation id>/tap-supply-chain/<appname>-tap-workload
    * <cloudformation id>/tap-supply-chain/<appname>-tap-workload-bundle 
13. Status of tanzu app: `tanzu apps workload get sample-app --namespace tap-workload`
### helpful commands
* list workloads : tanzu apps workload list -n tap-workload
### Cleaning an AWS 
* Leveraging [AWS Nuke](https://github.com/rebuy-de/aws-nuke)
