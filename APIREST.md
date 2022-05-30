# API REST

## Inicializar

Inicializar proyecto:

    npm init -y

Instalar express:

    npm i express

Instalar Nodemon como dependencia de desarrollo:

    npm i nodemon -D

Run proyecto:

    "dev": "npx nodemon index.js"
    "start": "node index.js"

Levantar servidor en puerto 3000:
<pre>
const express = require('express');
const app = express();
const port = 3000;

app.listen(port, () => {
    console.log('server on in port', port);
})
</pre>

