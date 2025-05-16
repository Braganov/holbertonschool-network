flowchart LR
    Browser((Browser))
    DNS[DNS Server]
    FW[Firewall]
    LB[Load Balancer]
    WS[Web Server]
    AS[Application Server]
    DB[(Database)]
    
    Browser -->|1. DNS Query| DNS
    DNS -->|2. IP Address| Browser
    Browser -->|3. HTTPS Request| FW
    FW -->|4. Filtered Traffic| LB
    LB -->|5. Route Request| WS
    WS -->|6. Process| AS
    AS -->|7. Query| DB
    DB -->|8. Data| AS
    AS -->|9. Response| WS
    WS -->|10. Web Page| LB
    LB -->|11. Response| FW
    FW -->|12. Secure Response| Browser