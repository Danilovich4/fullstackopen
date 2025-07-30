# Ejercicio 0.4 – Crear una nueva nota

Este diagrama muestra lo que sucede cuando un usuario escribe una nueva nota y hace clic en "Save" en la página `https://studies.cs.helsinki.fi/exampleapp/notes`.

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: El usuario escribe el texto en el campo de entrada

    browser->>browser: El usuario hace clic en "Save"
    Note right of browser: Se ejecuta una función JavaScript asociada al evento click

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: 302 Redirect
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML actualizado
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    server-->>browser: CSS file

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    server-->>browser: JS file

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    server-->>browser: JSON con la nueva nota incluida

    Note right of browser: El navegador renderiza la lista de notas incluyendo la nueva

