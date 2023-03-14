# coding-project-template

1. Export your namespace env

    export MY_NAMESPACE=sn-labs-$USERNAME

2. Build the guestbook app

    docker build . -t us.icr.io/$MY_NAMESPACE/guestbook:v1

3. Push the image to IBM Cloud Container Registry

    docker push us.icr.io/$MY_NAMESPACE/guestbook:v1

4. Verify that the image was pushed successfully.

    ibmcloud cr images

5. Apply the deployment

    kubectl apply -f deployment.yml

6. Open a new terminal and view your app

    kubectl port-forward deployment.apps/guestbook 3000:3000

7. Autoscale the Guestbook deployment

    kubectl autoscale deployment guestbook --cpu-percent=5 --min=1 --max=10

8. Check the current status

    kubectl get hpa guestbook

9. Open another new terminal and enter the below command to generate load on the app to observe the autoscaling

    kubectl run -i --tty load-generator --rm --image=busybox:1.35.0 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- <your app URL>; done"

10. Observe the repicas increasing

    kubectl get hpa guestbook --watch

11. Observe the details of the HPA

    kubectl get hpa guestbook

