0.4: New note diagram

```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Note over Browser: Typed "Hello" in inputbox and <br>clicked submit button
    Browser->>+Server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note over Server: Proccess save of Text <br> "Hello" to notes array
    
    activate Server
    Server-->>Browser: Send call to Refresh the Browser
    deactivate Server
    
    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Server
    Server-->>Browser: Return notes HTML document
    deactivate Server

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: Return main.css
    deactivate Server

    Note over Browser: Implement styles on main.css

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Server
    Server-->>Browser: Return main.js
    deactivate Server

    Note over Browser: Start Executing the js file

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: Return data.json
    deactivate Server

    Note over Browser: Execute the callback function to render the <br> Updated Notes
```
