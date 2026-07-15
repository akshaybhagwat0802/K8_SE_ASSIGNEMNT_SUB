## Steps <br>
1) Launch an ec2 intance in aws cloud having an ubuntu image .<br>
   1) image - Ubuntu .<br>
   2) instance type - t3.micro.<br>
   3) security group having :-
      1) ssh = 22 <br>
      2) http = 80 <br>
      3) https= 443 <br>

2) install docker
   ~~~ bash
   sudo apt update &&
   sudo apt install docker.io -y &&
   systemctl start docker &&
   systemctl enable docker &&
   
   ~~~
   ~~~ bash
   sudo usermod -aG docker $USER
   newgrp docker 
   ~~~
3) intall kubernetes
   ~~~ bash
   curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
   ~~~
   ~~~bash
   chmod +x kubectl
   ~~~
   ```bash
   sudo mv kubectl /usr/local/bin/
   ```
   ```bash
   kubectl version --client
   ```
4) install kind
   ```bash
   curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
   ```
   ```bash
   chmod +x kind
   ```
   ```bash
   sudo mv kind /usr/local/bin/
   ```
   ```bash
   kind version
   ```
 5) create kubernetes cluster
    ```bash
    kind create cluster --name imesh
    ```
    1) check nodes
       ```bash
       kubectl get nodes
       ```
     output
    ```bash
    NAME                  STATUS   ROLES           AGE   VERSION
    imesh-control-plane   Ready    control-plane   92s   v1.36.1
  ```
