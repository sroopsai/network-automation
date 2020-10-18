# Network Automation :rocket:

### Aim of the project

1. Deploy nginx on webservers and haproxy on load-balancer.
2. The load-balancer should be able to successfully load balance the client requests.
3. Serve a simple web page deployed on web servers through load-balancer depending upon the balance.

### Setup

### Required network to be created

```
(Internet)---> HAProxy	
		+--->A	|--
		+--->B	| |---> (Internal Private Network (10.0.1.0/27)	
		+--->C	|--
(Internet) --->	Bastion
```

#### Deployment of nginx into webservers and haproxy load balancer into haproxy server.

1. Deploy nginx servers to targeted webserver hosts and required php packages also to targeted webserver hosts.
2. Configure nginx servers on webserver hosts, restart the servers.
3. Deploy haproxy to targeted load balancer hosts.
4. Configuration file for haproxy written initially using Jinja2 templating engine, which renders the dynamic information of hosts. Here, it renders the hosts ip addresses. All templates rendered using Jinja2 templating engine are placed under templates directory.
5. Restart haproxy servers.
6. Command to run the playbook.
```bash
ansible-playbook -i hosts site.yaml
```

#### Testing 
1. A test script(test.sh.j2) has been written placed under templates directory. The task for running the test was included at the end of the playbook.

