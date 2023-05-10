# serverAda-2

// A partir de este archivo se va a ejecutar toda la aplicación

//Importamos http
const http = require('http');
const port = 3000;
const host = 'localhost';

/**
 * req -> request(solicitud): Es la solicitud que ingresa al servidor
 * 
 * res -> response(respuesta): Es la respuesta que el servidor entrega al cliente
 */
const server = http.createServer((req, res) => {

    /**
     * tipo de solicitud = req.method
     * 
     * url = direccion = req.url
     */
    if (req.method === 'GET' && req.url === '/users') {
        // Funcionará cuando la solicitud sea de tipo GET y quiera acceder a usuarios
        res.statusCode = 200;
        res.end('Accediste a usuarios')

        /**
         * voy a la base de datos y la base de datos me responde que no encontró al usuario
         * si encuentra usuario
         *  statusCode = 200
         * sino
         *  statusCode = 404
         */
    } else if(req.method === 'POST' && req.url === '/users') {
        res.statusCode = 200;
        res.end('Creación de usuarios')
    }else {
        res.statusCode = 404;
        res.end('Recurso no encontrado')
    }
})

// Encendemos el servidor con la función listen
server.listen(port, host, () => {
    console.log('Servidor encendido')
})
