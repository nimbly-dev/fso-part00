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

0.5: Single page app diagram

```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Note over Browser: Visit the Page
    Browser->>+Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate Server
    Server-->>Browser: Return the DOC html file.
    deactivate Server

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: Return main.css
    deactivate Server

    Note over Browser: Implement styles on main.css

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate Server
    Server-->>Browser: Return spa.js
    deactivate Server

    Note over Browser: Start Executing the js file

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: Return data.json
    deactivate Server

    Note over Browser: Execute the callback function to render the <br> Notes
```
0.6: New note in Single page app diagram

```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Note over Browser: Typed "Hello" on text box <br> then Click submit
    
    activate Browser
    Browser --> Browser: Push "Hello" to notes list using <br> notes.push() method
    deactivate Browser

    activate Browser
    Browser --> Browser: Rerender the notes list
    deactivate Browser

    Browser->>+Server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    
    Note over Server: Process the saving of note
    
    activate Server
    Server-->>Browser: Return 201 Response <br> {'message':'note created'}
    deactivate Server
```
