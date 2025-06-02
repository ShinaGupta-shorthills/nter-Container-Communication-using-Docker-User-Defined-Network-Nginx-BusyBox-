# Inter-Container-Communication-using-Docker-User-Defined-Network-Nginx-BusyBox
A simple Docker-based project to demonstrate how containers can communicate over a custom bridge network using container names.


# 🐳 Docker Network Communication Example (Nginx & BusyBox)

This project demonstrates simple inter-container communication using a **user-defined Docker bridge network**. It involves launching two containers:

- **Nginx**: Acts as a lightweight web server.
- **BusyBox**: A minimal container used to test network connectivity via `ping`.

---

📌 Objective
To show how containers on the same **user-defined Docker network** can communicate using container names.

 Steps to Run the Project
1️⃣ Create a user-defined bridge network
docker network create my-custom-network
2️⃣ Run an Nginx container on the network
docker run -d --name web-server --network my-custom-network nginx
3️⃣ Run a BusyBox container and ping the Nginx container
docker run -it --rm --network my-custom-network busybox
Inside the BusyBox shell, run:
ping web-server
You should see successful replies like:
PING web-server (172.18.0.2): 56 data bytes
64 bytes from 172.18.0.2: seq=0 ttl=64 time=0.123 ms
This confirms that container-to-container communication works via container name resolution.

🎯 Benefits of Using a User-Defined Docker Network
Feature	Benefit
DNS-based discovery	Communicate using container names instead of IPs
Traffic isolation	Containers on the network are isolated from others
Enhanced control	Easily manage and connect containers to the network
Secure communication	No exposure to external networks unless explicitly set

🧼 Cleanup
To remove the container and network:
docker rm -f web-server
docker network rm my-custom-network

🔍 Additional Info
This setup is ideal for:

Beginners learning Docker networking
Validating basic service connectivity
Prototyping container communication scenarios
Preparing for Docker/Kubernetes/DevOps interviews

📁 Author
Shina Gupta
DevOps Enthusiast | CKA Certified | 
