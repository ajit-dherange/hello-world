# AZ AKS Hello-World Application

1.	Login to Azure Portal

2.	Open AZ Cloud shell and Create Resource group “myResourceGroup” & AKS Cluster “myAKSCluster” with one node

   $ az group create --name myResourceGroup --location centralus 
   
   $ az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 1 --node-vm-size Standard_B2s --enable-addons monitoring --generate-ssh-keys

3.	Create new user “aksuser01” in Azure Active Directory (goto Azure Active Directory and select new user)

4.	Assign “Contributor” role to new user on AKS Cluster “myAKSCluster” and required resource groups (goto resource groep and select IAM)

5.	Login to Azure Portal with new user “aksuser01” and opened cloud shell

6.	Connect to the AKS cluster “myAKSCluster“ using commands from Azure Portal and create Pod with “hello-world“ Container conataining  “hello-world” application image 
& Load Balance Service “hello-world-load-balancer“ using manifest files 

    $ kubectl get nodes

    $ kubectl get pods

    $ kubectl apply -f ajit-hello_world-depl_v2.yml

    $ kubectl apply -f ajit-hello_world-svc_v2.yml

    $ kubectl get nodes

    $ kubectl get pods

7.	Extract  external IP from the service “hello-world-load-balancer” and browse the “hello-world” app in new tab

    $ kubectl get service hello-world-load-balancer –watch

8.	Scaling Pods to 3 and browse the “hello-world” app again in new tab

    $ kubectl scale --replicas=3 deployment/hello-world

9.	Scale down Pods to 1 and connect to a Pod

    $ kubectl scale --replicas=1 deployment/hello-world
    
10. Connect to the pod using SSH

    $ kubectl get pods -o wide

    $ kubectl exec --stdin --tty hello-world-6b58f8d7f-v96ln -- sh
    
 
 Note: Delete all resources created on Azure as soon as test complete and result shown to avoid utilization charges, new lab can be setup in minutes using above caommads 
