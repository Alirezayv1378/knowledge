# Proxy
- Sits between client and server and handles different kind of tasks. 
- One of the main goal of proxies is to hide client/server real IP and add protection level.

## Different Type of Proxies
1. **Forward Proxy:** Protects and represents the client by:
	- Hiding client identity.
	- Filtering outbound traffic.
	- ISP caching
	- Bypass geo restrictions
2. **Reverse Proxy(like NGINX):** Protects and represents the server and used for:
	- Load balancing
	- Hide server IPs
	- SSL termination
	- DDoS protection
	- Caching
	- API gateway logic
	
3. **Transparent Proxy** is a network device or software that intercepts traffic without requiring client configuration changes. and uses for:
	- Content caching
	- Web filtering
	- Logging/monitoring
	- Malware filtering
	- Traffic shaping
	