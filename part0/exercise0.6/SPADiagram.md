## 0.5 + 0.6 SPA Diagram
'''mermaid
sequenceDiagram
    participant browser
    participant server

    %% --- Initial SPA Load ---

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: JS runs and fetches existing notes

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON with notes
    deactivate server

    Note right of browser: Notes rendered on page (no reload)

    %% --- Creating a New Note in SPA ---

    Note right of browser: User writes note and clicks Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa\nJSON: { content: "new note", date: "..." }
    activate server
    server-->>browser: 201 Created
    deactivate server

    Note right of browser: JS updates UI with new note, no reload
