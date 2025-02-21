Provide your solution here:

**I. How we would troubleshoot the issue:**
1. Check System Resource Usage:

- Use top, htop, ps aux | grep nginx or free -h to get a real-time view of running processes and focus con NGINX process

2. Review NGINX configuration:
	
- Check the NGINX config files in /etc/nginx/nginx.conf and files in /etc/nginx/sites-available/
- Look for these key areas: worker_processes, worker_connections, client_max_body_size, proxy_cache 

3. Check and Analyze Disk and NGINX Logs:
4. Check Upstream Services: Investigate if the upstream services are sending unusually large responses. Optimize the upstream services if possible.


Look into /var/log/nginx/error.log, /var/log/nginx/access.log and /var/log/syslog

**II. Potential Root Causes, Impacts, and Recovery**
**1.Scenario 1**: Memory Leak in NGINX or Misconfiguration

1.1.Cause: 
- A bug in NGINX itself or a third-party module could be causing a memory leak 
- NGINX is configured with an excessive number of worker_processes or worker_connections, or the system is experiencing a sudden spike in traffic.
1.2.Impact: High memory usage, potentially leading to the VM becoming unresponsive or crashing (Out of Memory error). This will interrupt service to your upstream services.
1.3. Recovery:
- Reduce worker_processes and worker_connections: Carefully adjust these values in the NGINX configuration file. Start by reducing them incrementally, then reload NGINX (sudo systemctl reload nginx). Monitor memory usage after each adjustment.
- Reduce buffer sizes in client_body_buffer_size & proxy_buffers.
- Investigate Traffic Spike: If the issue is due to a traffic spike, consider scaling up your infrastructure (e.g., adding more NGINX instances, using a load balancer).
- Update NGINX: sudo apt update && sudo apt upgrade nginx

**2.Scenario 2**: High Traffic or DDoS Attack
2.1.Cause: 
- Spike in incoming connections.
- Frequently Many requests from one or few IP addresses within a short time.
2.2.Impact: Overloaded NGINX instance leading to high memory usage and potential downtime.
2.3.Recovery:
- Block Malicious IPs by FW iptables
- Enable Rate Limiting in NGINX
- Implement Cloudflare or AWS WAF to offload traffic filtering.
- Auto-Scaling 
