# Network Automation

### Aim of the project

1. Deploy nginx on webservers and haproxy on load-balancer.
2. The load-balancer should be able to successfully load balance the client requests.
3. Serve a simple web page deployed on web servers through load-balancer depending upon the balance.

### Setup

### Required network to be created

```
(Internet) ---> HAProxy	
		+--->A	|--
		+--->B	| |---> (Internal Private Network (10.0.1.0/27)	
		+--->C	|--
(Internet) --->	Bastion
```

#### Deployment of nginx into webservers and haproxy load balancer into haproxy server.

1. The deployment of nginx into webservers is automated using Ansible.
2. YAML script (`site.yaml`) will be used by Ansible to deploy the required packages `nginx, php, php-fpm` into webservers specified in the inventory file `hosts`.
3. Tha same YAML script will be used by Ansible to deploy the required package `haproxy` into load-balancer servers specified in the inventory file `hosts`.
4. `default` and `haproxy.cfg` are templated using Jinja2 template engine which will render the templates during runtime of ansible-playbook.
5. Command:
```bash
ansible-playbook -i hosts site.yaml
```
