##Windocks SQL Server Proxy \

The Windocks SQL Server Proxy provides secure Kubernetes support for provisioning and managing 
Windocks SQL Server containers.   Each Proxy service proxies’ TCP traffic to a Windocks SQL Server
container, using a fixed port, and deletes and cleans up Windocks SQL Server containers and data 
when the proxy service deployment is removed.  The design also supports persistent Windocks 
containers.

The deployment and service YAML files referenced below reflect testing on Google cloud.  Some 
modifications will be needed for use on AWS, Azure, or other Kubernetes services.

#Prerequisites

The service requires a Windocks server at a known IP address, the windocks/windocks-sql-server-proxy 
image, deployment and service YAML files, and a secrets.sh file.

The YAML files and secrets file are available at https://github.com/WinDocks/Windocks_SQL_Proxy_YAML

#Instructions

Setup a Windocks server, and update the YAML and Secrets files with the appropriate IP address, SQL
Server image name, and other credentials needed for these files.   

RUN:
>sh secrets.sh
>kubectl create -f sqlproxy-secure-service.yaml
>kubectl create -f sqlproxy-secure-deployment.yaml

Access the SQL Server container using SSMS using the external IP address of the Proxy service, followed 
by the fixed port using a comma separator (123.54.76.210,3087), using the assigned sa and sapassword.  

Contact support@windocks.com
