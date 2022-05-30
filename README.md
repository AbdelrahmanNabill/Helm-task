# Helm-tasks

## First:
- Start Minikube cluster 

## Task 1:

### Steps to Deploy the application:

- dockerize the application.
- build the image.

- * Create image from DockerFile by command.
```sh
docker build -t <image_name> .
```
- push the image to Google container registry.
- push redis image to the same gcr.

* Command used to push image from local machine to GCR .
```sh
docker tag <image_name> gcr.io/<project_name>/<image_name>
```
```sh
docker push gcr.io/<project_name>/<image_name>
```

![Screenshot from 2022-05-30 21-47-17](https://user-images.githubusercontent.com/95745245/171065173-69615d25-2870-4702-bcf6-fe6b2f14ce08.png)

- Create helm charts for the python application and redis database.

```sh
helm create <chart-name>
```
- install the created charts.

```sh
helm install <release-name> <chart-name>
```
![Screenshot from 2022-05-31 00-06-12](https://user-images.githubusercontent.com/95745245/171066025-70b4a651-1724-4705-a6bb-71cd9aab0627.png)

- accessing the app through minikube ip and the exposed NodePort 

![Screenshot from 2022-05-31 00-06-51](https://user-images.githubusercontent.com/95745245/171066203-0452665b-3fc9-40e5-9d8b-b689e101ff4b.png)

<hr> 

## Task 2:

## Steps to Deploy promethues on the cluster using helm

- Add the repo 

```sh
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

- Install Prometheus Kubernetes

```sh
 helm install prometheus prometheus-community/kube-prometheus-stack
 ```
 ![Screenshot from 2022-05-31 00-20-50](https://user-images.githubusercontent.com/95745245/171066494-e2ccd50c-4377-4714-9c78-95b10eafba5f.png)
 
![Screenshot from 2022-05-31 00-25-15](https://user-images.githubusercontent.com/95745245/171066503-a59b8691-0530-4596-aeb0-a05337debdf2.png)
 
- Kubernetes Prometheus Port Forward

```sh
kubectl port-forward deployment/prometheus-grafana 3000
```
![Screenshot from 2022-05-31 00-28-58](https://user-images.githubusercontent.com/95745245/171066515-812ae750-8972-4ebd-a736-39acbaf45513.png)

![Screenshot from 2022-05-31 00-29-00](https://user-images.githubusercontent.com/95745245/171066525-ef86937c-5217-4653-bfd4-05a0baa8af2c.png)

