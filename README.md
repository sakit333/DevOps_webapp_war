## sample playbook
---
```bash
docker build -t $JOB_NAME:v1.$BUILD_ID .
docker tag $JOB_NAME:v1.$BUILD_ID sakit333/$JOB_NAME:v1.$BUILD_ID
docker tag $JOB_NAME:v1.$BUILD_ID sakit333/$JOB_NAME:latest
docker push sakit333/$JOB_NAME:v1.$BUILD_ID
docker push sakit333/$JOB_NAME:latest
docker rmi $JOB_NAME:v1.$BUILD_ID sakit333/$JOB_NAME:v1.$BUILD_ID sakit333/$JOB_NAME:latest
```
---
```bash
---
- hosts: all
  become: true
  tasks:
      - name: stop previous version docker
        shell: docker stop qspider
      - name: remove stopped container
        shell: docker rm -f qspider	 
      - name: remove docker images
        shell: docker image rm -f sakit333/project-4
       - name: create docker image
        shell: docker run -it -d -p 8889:8080 sakit333/project-4:v1.3
```
---
