# System Flow Diagram: Google.com Request

```mermaid
graph LR
    Browser[Browser]
    DNS[DNS Server]
    FW[Firewall]
    LB[Load Balancer]
    WS[Web Server]
    AS[Application Server]
    DB[(Database)]
    
    %% DNS Resolution
    Browser -->|1. DNS Query| DNS
    DNS -->|2. IP Address| Browser
    
    %% HTTPS Request
    Browser -->|3. HTTPS Request\nPort 443| FW
    
    %% Request Flow
    FW -->|4. Filtered Traffic| LB
    LB -->|5. Route Request| WS
    WS -->|6. Dynamic Content\nRequest| AS
    AS -->|7. Data Query| DB
    
    %% Response Flow
    DB -->|8. Data| AS
    AS -->|9. Generated Page| WS
    WS -->|10. Response| LB
    LB -->|11. Load Balanced\nResponse| FW
    FW -->|12. Secure Response| Browser
    
    %% Styling
    classDef secure fill:#f9f,stroke:#333,stroke-width:2px;
    classDef server fill:#bbf,stroke:#333,stroke-width:2px;
    
    class FW,LB secure;
    class WS,AS,DB server;
    
    %% Notes
    subgraph Security
        FW
        note1[Encrypted SSL/TLS Traffic]
    end
    
    subgraph "Load Distribution"
        LB
        note2[Request Distribution]
    end
    
    subgraph "Server Infrastructure"
        WS
        AS
        DB
    end
```

This diagram illustrates the complete flow of a request to www.google.com:

1. **DNS Resolution**: Browser queries DNS server to convert domain to IP
2. **Firewall**: Secure traffic filtering on port 443
3. **Load Balancer**: Distributes incoming requests
4. **Web & Application Servers**: Process the request
5. **Database**: Stores and retrieves data

The entire communication is encrypted using HTTPS/SSL, represented by secure connections through the firewall.