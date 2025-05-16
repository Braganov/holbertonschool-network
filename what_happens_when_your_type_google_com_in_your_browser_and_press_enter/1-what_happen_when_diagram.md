sequenceDiagram
    participant Browser
    participant DNS
    participant Firewall
    participant LoadBalancer
    participant WebServer
    participant AppServer
    participant Database

    Browser->>DNS: DNS Query (www.google.com)
    DNS-->>Browser: IP Address Response
    Browser->>Firewall: HTTPS Request (Port 443)
    Firewall->>LoadBalancer: Forward Encrypted Traffic
    LoadBalancer->>WebServer: Route to Available Server
    WebServer->>AppServer: Process Request
    AppServer->>Database: Query Data
    Database-->>AppServer: Return Data
    AppServer-->>WebServer: Generated Page
    WebServer-->>LoadBalancer: Web Page Response
    LoadBalancer-->>Firewall: Forward Response
    Firewall-->>Browser: Return HTTPS Response