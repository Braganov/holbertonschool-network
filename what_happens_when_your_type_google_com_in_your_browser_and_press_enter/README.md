# What Happens When You Type google.com

This project explains the complete flow of what happens when you type https://www.google.com in your browser and press Enter.

## Flow Diagram

```mermaid
sequenceDiagram
    participant Browser
    participant DNS
    participant Firewall
    participant LoadBalancer
    participant WebServer
    participant AppServer
    participant Database

    Browser->>DNS: 1. DNS Query for www.google.com
    DNS-->>Browser: 2. Returns IP Address

    Note over Browser,DNS: DNS Resolution

    Browser->>Firewall: 3. HTTPS Request (Port 443)
    Note over Browser,Firewall: Encrypted Traffic (SSL/TLS)
    
    Firewall->>LoadBalancer: 4. Forward Request
    Note over LoadBalancer: Request Distribution
    
    LoadBalancer->>WebServer: 5. Route to Available Server
    
    WebServer->>AppServer: 6. Process Request
    
    AppServer->>Database: 7. Query Data
    Database-->>AppServer: 8. Return Data
    
    AppServer-->>WebServer: 9. Generated Page
    WebServer-->>LoadBalancer: 10. Web Page Response
    LoadBalancer-->>Firewall: 11. Forward Response
    Firewall-->>Browser: 12. HTTPS Response

    Note over Browser: Render Page
```

## Components Overview

1. **DNS Resolution**
   - Converts www.google.com to IP address
   - Involves DNS recursive resolvers and authoritative servers

2. **HTTPS/SSL**
   - Encrypted connection on port 443
   - TLS handshake for secure communication

3. **Firewall**
   - Filters incoming/outgoing traffic
   - Enforces security policies

4. **Load Balancer**
   - Distributes traffic across servers
   - Ensures high availability

5. **Web Server**
   - Handles HTTP requests
   - Serves static content

6. **Application Server**
   - Processes dynamic requests
   - Implements business logic

7. **Database**
   - Stores and retrieves data
   - Handles queries from app server