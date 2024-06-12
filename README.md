## Build Image

1️⃣ build image

```shell
   docker build -t mhmud/api_app:v1 -f Dockerfile .
```

2️⃣ Push image to DockerHub

```shell
   docker push mhmud/api_app:v1
```

3️⃣ deploy the postgres DB , the app on K8s .

```shell
   helm repo add api-app https://mahmoudaboghadeer93.github.io/api-app/charts
   helm install ${Release_Name} --namespace ${Namespace_Name} api-app/api-app-chart --version 0.1.0 \
   --set image.repository=mhmud/api_app \
   --set image.tag=v1
```

4️⃣ Test the our APP :
   
   - make port forward for api-svc to test it locally using Postman to make HTTP requests
     
```shell
   kubectl -n test port-forward svc/api-app-svc 4000:4000
```   

   - Create new user using this endpoint (http://localhost:4000/api/flask/users) using POST Request on Postman like this:

<img width="839" alt="Screenshot 2024-06-12 at 1 28 50 PM" src="https://github.com/mahmoudaboghadeer93/api-service/assets/69244659/abd2f8f3-37e4-4744-9855-7c91991bae88">



   - Then you can list the created users using GET Request (http://localhost:4000/api/flask/users) :

<img width="836" alt="Screenshot 2024-06-12 at 1 36 39 PM" src="https://github.com/mahmoudaboghadeer93/api-service/assets/69244659/3a06c21d-bb34-468c-8a97-bb57bee40b37">


   - Also you can get the list of users from DB using:

<img width="968" alt="Screenshot 2024-06-12 at 1 39 34 PM" src="https://github.com/mahmoudaboghadeer93/api-service/assets/69244659/463ab117-fb5e-42f9-a55f-d54d42ca2e7d">


   - update and delete a user:
      - You can update a user, but making a PUT request to http://localhost:4000/api/flask/users/3

      - You can delete a user, but making a DELETE request to http://localhost:4000/api/flask/users/3

<img width="800" alt="Screenshot 2024-06-12 at 1 43 37 PM" src="https://github.com/mahmoudaboghadeer93/api-service/assets/69244659/31a637ce-60be-4d06-bc54-f57f1a8b3723">


🎉 We are done. 🎉

         
