# API REST

## 1. Levantar servidor

Inicializar proyecto:

    npm init -y

Instalar express:

    npm i express

Crear archivo app.js 

<pre>
const express = require('express');
const app = express();
const port = 3000;

app.listen(port, () => {
    console.log('server on in port', port);
})
</pre>

Instalar Nodemon como dependencia de desarrollo:

    npm i nodemon -D

Run proyecto:

    "dev": "npx nodemon index.js"
    "start": "node index.js"



