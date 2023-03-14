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