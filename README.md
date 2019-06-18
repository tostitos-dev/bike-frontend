# bike-frontend

## Vista previa

*Lista de estaciones y sus últimos valores de ocupación:*

![alt text](https://raw.githubusercontent.com/tostitos-dev/bike-frontend/master/src/assets/Screenshot%20from%202019-06-18%2018-19-48.png | width=100)

*Valores actuales de la red*

![alt text](https://raw.githubusercontent.com/tostitos-dev/bike-frontend/master/src/assets/Screenshot%20from%202019-06-18%2018-20-02.png | width=100)

*Gráfico de la última hora (uso vs tiempo)*

![alt text](https://raw.githubusercontent.com/tostitos-dev/bike-frontend/master/src/assets/Screenshot%20from%202019-06-18%2018-20-07.png | width=100)

## General
- Versión node: 10.16.0
- Versión vue: 2.6.1

## Instrucciones de uso

- Añadir .env con la API KEY de google
- Ejecutar npm install
- Ejecutar npm run serve

## Descripción

La aplicación cuenta con dos views, Home y Stations. La primera muestra los KPIS actuales de la red, un gráfico resumen de ellos y un gráfico de la última hora en función de su uso en el tiempo. La segunda vista muestra una lista de tarjetas, cada una es un estacionamiento de bicicletas y contiene los últimos indicadores, más un mapa estático de su ubicación.

Los principales componentes utilizados:
- Bootstrap Vue para los estilos.
- Axios para el consumo de la aplicación backend.
- Vue-chartjs para el despliegue de los gráficos.
- Vue Static Map para pintar los mapas de manera estática.


