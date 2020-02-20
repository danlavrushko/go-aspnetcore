# Go aspnet core!
Test project to try asp.net core docker images and k8s.

# Setup 
1. mkdir src
1. cd src
1. dotnet new web -n GoAspNetCore.Web
1. dotnet new sln -n GoAspNewCore
1. dotnet sln add .\GoAspNetCore.Web\GoAspNetCore.Web.csproj
1. copy Dockerfile, .dockerignore

# Build, publish and manage docker image
1. docker build -t danlavrushko/go-aspnetcore:1.0.0 .
1. docker image push danlavrushko/go-aspnetcore:1.0.0
1. docker run -d --rm -p 5000:80 --name go-aspnetcore danlavrushko/go-aspnetcore:1.0.0
1. docker stop go-aspnetcore
1. docker rm go-aspnetcore

# k8s
1. kubectl run hello-world --image=danlavrushko/go-aspnetcore:1.0.0
1. kubectl logs <pod>
1. kubectl expose deployment hello-world --port=80 --target-port=80
1. kubectl get endpoints hello-world
1. kubectl get service hello-world -o yaml --export > service-hello-world.yaml
1. kubectl get deployment hello-world -o yaml --export > deployment-hello-world.yaml
1. vi deployment-hello-world.yaml
1. kubectl apply -f deployment-hello-world.yaml
