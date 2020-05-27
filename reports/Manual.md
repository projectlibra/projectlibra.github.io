# User Manual for LIBRA

## Usage of LIBRA

## Build and Deployemnt

This section explains the procedure of building and deploying LIBRA from the github source files.

There will be many code snippets that explains the building process. each snippet has the following format:


- First the github repository has to be obtained.

~~~
$ git clone https://github.com/projectlibra/projectlibra.git
~~~

- Once you clone the repository, you will encounter a file structure like the following:

~~~
/projectlibra
├── README.md
├── libra-backend
└── libra-frontend
~~~

### Building the Client

The client is written in React JS and the build procedure is fairly simple.

#### Install React JS

If React JS is not currently installed on your system, we consult you to the [official React JS documentation](https://reactjs.org/docs/create-a-new-react-app.html) for the installation process.

#### Install dependencies

You can install all dependencies required for the client using the following snippet:

~~~
$ cd libra-frontend
$ npm install
~~~

#### Setting up the HOST IP

You must change the host IP embedded in the file **host.js** for the backend server that you are running:

~~~
var host = 'Backend Server IP:PORT'
~~~

#### Runnning the client

You can run the client via npm and the landing page will be displayed in the default browser:

~~~
$ npm start
~~~