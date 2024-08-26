## sample playbook
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
