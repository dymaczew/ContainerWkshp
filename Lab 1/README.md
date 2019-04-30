# Lab 1. Set up and deploy your first application

Learn how to push an image of an application to IBM Cloud Container Registry and deploy a basic application to a cluster.

# 0. Install Prerequisite CLIs and Provision a Kubernetes Cluster

If you haven't already:
1. Install the CLIs and Docker, as described in [Lab 0](../Lab%200/README.md).


# 1. Push an image to IBM Cloud Container Registry

To push an image, we first must have an image to push. We have
prepared several `Dockerfile`s in this repository that will create the
images. We will be running the images, and creating new ones, in the
later labs. 

This lab uses the Container Registry built in to IBM Cloud, but the
image can be created and uploaded to any standard Docker registry to
which your cluster has access.

1. Download a copy of this repository:

1a. [Clone or download](https://github.com/dymaczew/ContainerWkshp) the GitHub repository associated with this course

2. Change directory to Lab 1: 

   ```cd "Lab 1"```

3. Log in to the IBM Cloud Privat CLI: 

   ```bx pr login -a https://mycluster.icp:8443 --skip-ssl-validation```
   
4. Build the Docker image in this directory with a `1` tag (replacing my_namespace with appropriate namespace you have access to)

   ```docker build --tag mycluster.icp:8500/<my_namespace>/hello-world:1 .```

5. Verify the image is built: 

   ```docker images```

6. Now push that image up to IBM Cloud Private Container Registry: 

   ```docker push mycluster.icp:8500/<my_namespace>/hello-world:1```

You are now ready to use Kubernetes to deploy the hello-world application.

# 2. Deploy your application

1. Setup a kubectl context (it should be already set after issuing **bx pr login** command)

2. Start by running your image as a deployment: 

   ```kubectl run hello-world --image=mycluster.icp:8500/<my_namespace>/hello-world:1```

   This action will take a bit of time. To check the status of your deployment, you can use `kubectl get pods`.

   You should see output similar to the following:
   
   ```
   => kubectl get pods
   NAME                          READY     STATUS              RESTARTS   AGE
   hello-world-562211614-0g2kd   0/1       ContainerCreating   0          1m
   ```

3. Once the status reads `Running`, expose that deployment as a service, accessed through the IP of the worker nodes.  The example for this course listens on port 8080.  Run:

   ```kubectl expose deployment/hello-world --type="NodePort" --port=8080```

4. To find the port used on that worker node, examine your new service: 

   ```kubectl describe service <name-of-deployment>```

   Take note of the "NodePort:" line as `<nodeport>`

5. Login to any of the custler nodes.

6. You can now access your container/service using `curl localhost:<nodeport>` . If you see, "Hello world! Your app is up and running in a cluster!" you're done!

When you're all done, you can either use this deployment in the [next lab of this course](../Lab%202/README.md), or you can remove the deployment and thus stop taking the course.

1. To remove the deployment, use `kubectl delete deployment hello-world`. 
2. To remove the service, use `kubectl delete service hello-world`.
