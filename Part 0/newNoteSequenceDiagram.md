sequenceDiagram
  actor User
  participant Browser
  participant Server

  User->>Browser: Enter new note
  
  Note right of User: The user clicks on the form and enters a new note

  Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
  Server-->>Browser: HTTP 302 (URL Redirection)
  
  Note over Server: The server responds with a URL redirect request and the browser makes an HTTP GET request to the new address

  Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/note
  note over Browser: The browser reloads the page, repeating the first sequence

  Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
  activate Server
  Server-->>Browser: HTML document
  deactivate Server

  Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
  activate Server
  Server-->>Browser: the css file
  deactivate Server

  Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
  activate Server
  Server-->>Browser: the JavaScript file
  deactivate Server

  Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
  activate Server
  Server-->>Browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
  deactivate Server
