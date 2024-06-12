## Build Image

1️⃣ build image

```shell
   docker build -t mhmud/api_app:v1 -f Dockerfile .
```

2️⃣ Push image to DockerHub

```shell
   docker push mhmud/api_app:v1
```
3️⃣ use this image inside the deployment file for our API-APP

4️⃣ deploy the postgres DB , the app on K8s .

```shell
   cd k8s-yaml/
   kubectl -n test apply -f postgres/
   kubectl -n test apply -f api-app/
```

5️⃣ Test the our APP :
   
   - make port forward for api-svc to test it locally using Postman to make HTTP requests
     
```shell
   kubectl -n test port-forward svc/api-app-svc 4000:4000
```  

   - Create new user using this endpoint (http://localhost:4000/api/flask/users) using POST Request on Postman like this:

<img width="839" alt="Screenshot 2024-06-12 at 1 28 50 PM" src="https://github.com/mahmoudaboghadeer93/api-app/assets/69244659/b2819020-3b3c-4366-b83f-fd992150ac7d">


   - Then you can list the created users using GET Request (http://localhost:4000/api/flask/users) :

<img width="836" alt="Screenshot 2024-06-12 at 1 36 39 PM" src="https://github.com/mahmoudaboghadeer93/api-app/assets/69244659/02b290e0-53ba-4309-b36c-23f23a6d8d7d">


   - Also you can get the list of users from DB using:

<img width="968" alt="Screenshot 2024-06-12 at 1 39 34 PM" src="https://github.com/mahmoudaboghadeer93/api-app/assets/69244659/fc6e52d8-2be5-4f69-aa4e-e6b6f8cafe08">


   - update and delete a user:
      - You can update a user, but making a PUT request to http://localhost:4000/api/flask/users/3

      - You can delete a user, but making a DELETE request to http://localhost:4000/api/flask/users/3

<img width="800" alt="Screenshot 2024-06-12 at 1 43 37 PM" src="https://github.com/mahmoudaboghadeer93/api-app/assets/69244659/756cabf2-1681-4129-a9f7-0cbdf747f0ed">

         
