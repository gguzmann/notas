# API REST

Iniciar Repositorio

`npm init -y`

`npm i express`


<code>
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.get('/', (req, res) => {
    res.send('Hola');
})


app.listen(port, () => {
    console.log('server on in port', port);
})


</code>

>`npm i nodemon -D`
