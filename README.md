
# Rails-Postgres Docker Pipeline with Kubernetes, ArgoCD, and Tekton

## Project Overview

This project sets up a **Ruby on Rails** application with **PostgreSQL** and automates deployment and CI/CD using **Docker**, **Kubernetes**, **ArgoCD**, and **Tekton**. The steps include building and Dockerizing a Rails app, deploying it to Kubernetes using Minikube, managing deployments with ArgoCD, and automating CI/CD with Tekton.

---

## Steps

### Step 1: Dockerize Ruby on Rails with PostgreSQL

In the first step, a simple **Ruby on Rails** application was built, featuring basic CRUD operations to create posts. The database used is **PostgreSQL**, running in a separate container.

### Access the App Locally

To access the app locally, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/repositoryname.git
   cd repositoryname
   
2. Install the dependencies:
   ```bash
   bundle install
   yarn install
   
3. Set up the database:
   ```bash
   rails db:create
   rails db:migrate
   
4. Run the Rails server:
   ```bash
   rails server

5. Open your browser and navigate to: http://localhost:3000/posts/new
   
- **Dockerfile**: We created a Dockerfile to containerize the Rails application.
- **docker-compose.yml**: Used to define and manage multi-container Docker applications for the Rails app and PostgreSQL.

**Commands to build and run the application**:
```bash
docker build -t rails-app .
docker-compose up
```

### Step 2: Deploy on Kubernetes with Minikube

The second step involved deploying the Dockerized application to a **Kubernetes** cluster using **Minikube** as the local cluster provider.

- **PostgreSQL** was deployed using a **StatefulSet** for persistence.
- The Rails app was deployed using a standard deployment configuration.

**Kubernetes Manifests**:
- `postgres.yaml`: Defines the Kubernetes configuration for PostgreSQL.
- `rails.yaml`: Defines the Kubernetes configuration for the Rails app.

**Commands to deploy the app**:
```bash
kubectl apply -f k8s/postgres.yaml
kubectl apply -f k8s/rails.yaml
```

### Step 3: GitOps with ArgoCD

The third step set up **ArgoCD** for continuous delivery using **GitOps** principles. All configurations and Kubernetes manifest files were pushed to a private GitHub repository.

- The **ArgoCD** application and configurations (`argocd-cm.yaml`, `argocd-rbac-cm.yaml`) were added to the repository.
- ArgoCD was configured to monitor the repository and automatically deploy the application to the Kubernetes cluster.

**ArgoCD Files**:
- `application.yaml`: Defines the application in ArgoCD.
- `argocd-cm.yaml`: ConfigMap for ArgoCD.
- `argocd-rbac-cm.yaml`: ArgoCD RBAC configuration.

### Step 4: CI/CD Pipeline with Tekton

In the final step, we set up a **Tekton** CI/CD pipeline to automate the build, test, and deployment of the application.

- The pipeline automatically builds the Docker image, pushes it to Docker Hub, and deploys the app to Kubernetes.

**Tekton Resources**:
- `pipeline.yaml`: Tekton pipeline configuration.
- `pipelinerun.yaml`: Tekton pipeline run configuration.
- `build-task.yaml`: Tekton task for building the Docker image.

---


## Running the Application

Once the application is deployed on Kubernetes, you can access it using the external IP of your Minikube cluster:

```bash
kubectl get svc
```

---

## Built With 🛠️

- **Ruby on Rails**: Framework for building the application.
- **Docker**: Containerization of the application.
- **Kubernetes**: Deployment and management of the app.
- **Minikube**: Local Kubernetes cluster.
- **ArgoCD**: GitOps for continuous delivery.
- **Tekton**: CI/CD automation for the app.
- **PostgreSQL**: Database used in the app.

---

## Authors

- **Nanda Kishore**  
  GitHub: [@nandakishore111](https://github.com/nandakishore111)  
  LinkedIn: [Nanda Kishore](https://www.linkedin.com/in/t-nanda-kishore?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3BqL9vO4QsRtW5sdq6dzqkjQ%3D%3D)

---

## 🤝 Contributions

Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

---

## Show Your Support

Give a ⭐️ if you like this project!


