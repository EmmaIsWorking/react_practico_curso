# React Course

## Index
- [React Course](#react-course)
  - [Index](#index)
  - [Dependencias:](#dependencias)
  - [Content](#content)
  - [How to clone](#how-to-clone)
  - [Installation](#installation)
  - [Preview](#preview)
  - [Notes](#notes)
  - [Concepts](#concepts)
    - [Tipos de componentes:](#tipos-de-componentes)
      - [Stateful](#stateful)
      - [Stateless & Presentatitonal:](#stateless--presentatitonal)
    - [Props](#props)
    - [Metodos de Ciclos de Vida](#metodos-de-ciclos-de-vida)
      - [Montaje:](#montaje)
      - [Actualización:](#actualizaci%c3%b3n)
      - [Demonstaje:](#demonstaje)
      - [Manejo de errores](#manejo-de-errores)

## Dependencias:
`npm install react react-dom`

Instalación de Babel y otras herramientas para que funcione con React:

`npm install @babel/core babel-loader @babel/preset-env @babel/preset-react --save -dev`

Configuración de Babel (.babelrc):

```
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react"
  ],
}
```

Webpack: 
Instalación de Webpack y algunos plugins:

```
npm install webpack webpack-cli html-webpack-plugin html-loader  --save-dev

```

Configuración de Webpack (webpack.config.js):


```
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  resolve: {
    extensions: ['.js', '.jsx'],
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
        },
      },
      {
        test: /\.html$/,
        use: {
          loader: 'html-loader',
        },
      },
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './public/index.html',
      filename: './index.html',
    }),
  ],
};
```

Script para ejecutar las tareas de Webpack (package.json):

```
{
  "scripts": {
    "build": "webpack --mode production"
  },
}

```

Instalación de Webpack Dev Server:

`npm install --save-dev webpack-dev-server`

Script para ejecutar el servidor de Webpack y visualizar los cambios en tiempo real (package.json):

```
{
  "scripts": {
    "build": "webpack --mode production",
    "start": "webpack-dev-server --open --mode development"
  },
}
```

`npx create-react-app @NameProyect`
## Content
## How to clone
## Installation
## Preview
## Notes
## Concepts

### Tipos de componentes:
Los nombres de nuestros componentes deben empezar con una letra mayúscula, al igual que cada nueva palabra del componente. Esto lo conocemos como Pascal Case o Upper Camel Case.

#### Stateful
son los más robustos de React. Los usamos creando clases que extiendan de React.Component. Nos permiten manejar estado y ciclo de vida (más adelante los estudiaremos a profundidad).

#### Stateless & Presentatitonal:
También tenemos componentes Stateless o Presentacionales. Los usamos creando funciones que devuelvan código en formato JSX (del cual hablaremos en la próxima clase).

### Props
Las Props son la forma de enviar y recibir información en nuestros componentes.



### Metodos de Ciclos de Vida
Todos los componentes en React pasan por una serie de fases que generalmente se denominan “Ciclo de Vida del componente” es un proceso que React hace en cada componente, en algunos casos no podemos verlos como un bloque de código y en otros podemos llamarlos en nuestro componente para asignar una actividad según sea el caso necesario.

Los componentes en react pasan por un Montaje, Actualización, Desmontaje y Manejo de errores.

[¿Qué son los métodos del ciclo vida?](https://platzi.com/clases/1651-react-ejs/22576-que-son-los-metodos-del-ciclo-vida/)
#### Montaje:
`Constructor()`

`getDerivedStateFromProps()`

`render()`

`ComponentDidMount()`

#### Actualización:
`getDerivedStateFromProps()`

`shouldComponentUpdate()`

`render()`

`componentDidUpdate()`

#### Demonstaje:
`componentWillUnmount()`

#### Manejo de errores
`getDerivedStateFromError()`