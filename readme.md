1. install tap: make sure you put cidr in rdp
https://aws.amazon.com/quickstart/architecture/vmware-tanzu-application-platform/
2. Setup aws cli
'aws configure'
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html
Get info from cloud gate
$Env:AWS_ACCESS_KEY_ID="ASIA34EJ7OKVMA4GPEUT"
$Env:AWS_SECRET_ACCESS_KEY="IQUfvMlnnZagN50RcuBfeb/kmUWqpjXF5DcKSbeg"
$Env:AWS_SESSION_TOKEN="IQoJb3JpZ2luX2VjEAUaCXVzLWVhc3QtMSJIMEYCIQCh2ItWckUunPHJl7+BDLxW1HkaWTPhyg9S/LhYn4ZevgIhANsq10nVBpmkMvH5IPrskjtQTPRDR24egrV5oZ1VZPHwKqECCF0QARoMODE2MzMzMTU3MDM0IgyirjsOYxfSTbfAVKUq/gHetyRWxOEv3UxVnfjXnA1acRPY03WHHg3xvqz4ySxejBhp9gkLColUrJtOHZytf6A0yk5xpChiuqscLz7bPzlSAvDG80czWip2ol/QpKXnHF6b4N3mgJXUS5nRrs6NRfIO/P+H5EZte0pMbSMtDW+KKn/1rqhN5pxn0q/fb0bbT3oa+gaPqjVVdg2bSDxLTjCxYQHTwzdN6cV76sKGBPD9+9ADHkw2rYnuWnRnsM+GID6EuMPMcdQQHrpyeeWevolLBR+JDNcri+FBIAZaJ8UkwBFe2oBtf/5A41r/LF24I4Z4JDkgOumrrXqbpAGCUaq81wmse+i3gIZlGCbpoTDliZ+XBjqcAccIFE5kK5UXMEnHzj2SEEr90S2V+jvSBWwqEFc4wd/Q8PeiUINk7ISWVZeD9zVPgRos+VAQpMhgLY7HYZ+UQ2daVBKQIFXH/1OyPnvjNxCPprF35kRaosfFNf7eVn4Yf6cLdOFfIyGFO03lMJqCLx+NTTsWmFvACED268Y959MDkIdt1lzwebBD4BecGiu0VnWQaZriK5GCaeQcRA=="


PS C:\Program Files\Microsoft Visual Studio\2022\Enterprise> $Env:AWS_DEFAULT_REGION="us-east-1"

3. aws sts get-caller-identity
3. setup vpn
https://labrlearning.medium.com/remote-access-to-aws-with-the-client-vpn-6c43cd740b8
https://medium.com/faun/how-to-create-aws-client-vpn-to-access-private-resources-f4cc2c0145e0

4. windows password:  )!rMojeiwGVTmuC4Osm1!(XL4aHHXpvF
5. add Route Table : https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/scenario-internet.html

6. https://aws.amazon.com/premiumsupport/knowledge-center/eks-cluster-connection/

aws eks --region us-east-1 update-kubeconfig --name eks-tap-cluster

#Deploy workload
tanzu apps workload apply -f config/workload.yaml --label apps.tanzu.vmware.com/has-tests=true --type web --yes