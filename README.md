Screenshots (in Markdown README.md) for CI Workflow (Part 1)

![image](https://user-images.githubusercontent.com/82182536/168405093-d294d8e1-b0d4-4d1f-9e84-96b6e6f85b61.png)

![image](https://user-images.githubusercontent.com/82182536/168405071-9115c394-33bc-4311-8e2d-47e683eac094.png)

Screenshots (in Markdown README.md) for CD Workflow (Part 2)

Created a new workflow that can build and deploy the spring-gumball image onto GKE
![image](https://user-images.githubusercontent.com/82182536/168409935-89f69e75-09ed-4dd2-97a8-e2bc781ace6f.png)

As I tried to create a release I kept getting an error when setting up google cloud
![image](https://user-images.githubusercontent.com/82182536/168410028-7e39f9df-2fa5-460d-b23d-ed38b62a8a35.png)
I realized that I needed to put the entire JSON syntax in the GKE_SA_KEY whereas I would just put the key and it would cause an error.

After that, I ran into another error. It had an error with credentials and permissions. It wouldn't do "container.clusters.get"
![image](https://user-images.githubusercontent.com/82182536/168410094-c314e7b5-93aa-43b1-983b-cd40567ad37c.png)

To fix I had to change the roles and add a Cluster Admin because it had permission "container.clusters.get" that I needed. I got the idea from slack via Andrew Johson. He provided the link https://serverfault.com/questions/1044638/sudden-permissions-denied-for-service-account which gave me the inspiration
![image](https://user-images.githubusercontent.com/82182536/168410237-cd4fabc8-b426-4f5e-aa12-8e039866a332.png)

Of course, I ran into another error. This time it involved publishing.
![image](https://user-images.githubusercontent.com/82182536/168410357-2f435d71-03a8-446d-ae48-f1bc0145e563.png)
![image](https://user-images.githubusercontent.com/82182536/168410558-c9c43ea9-5656-471f-ad91-6c4a12cd2aa4.png)
Turns out I had to change GKE_PROJECT from the name of the project to the actual Project ID on my dashboard. I got the idea here: https://stackoverflow.com/questions/62800603/pushing-the-docker-image-to-container-registry

After many tries, I got spring-gumball to deploy
![image](https://user-images.githubusercontent.com/82182536/168410703-812d93c8-62d0-4508-935f-daa268d52503.png)
![image](https://user-images.githubusercontent.com/82182536/168410709-9ad5f095-7d7a-485a-a89a-798bdd46518d.png)

![image](https://user-images.githubusercontent.com/82182536/168410721-b08393f5-b7de-4fe6-9724-c5701781f741.png)

Creating our ingress
![image](https://user-images.githubusercontent.com/82182536/168410764-c070309c-77e4-4334-8749-c5b3e4855ae7.png)
![image](https://user-images.githubusercontent.com/82182536/168410867-f2d20dc8-2ad8-4e68-917f-4620348aeafb.png)
![image](https://user-images.githubusercontent.com/82182536/168410879-61339005-484f-4ac4-a202-a3e37ca8c825.png)

The gumball webpage
![image](https://user-images.githubusercontent.com/82182536/168410883-5bd315ae-dcb9-48c7-a98f-3341a0b5768d.png)

















-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
# spring-gumball ci/cd example

### This example demonstrates the following two GitHub Workflows.

* https://help.github.com/actions/language-and-framework-guides/building-and-testing-java-with-gradle

* https://github.com/google-github-actions/setup-gcloud/tree/master/example-workflows/gke

### Build Dependencies

* Gradle 5.6
* JDK 11
