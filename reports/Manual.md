# User Manual for LIBRA

## Usage of LIBRA

## Build and Run

This section explains the procedure of building and deploying LIBRA from the github source files.

There will be many code snippets that explains the building process. each snippet has the following format:


- First the github repository has to be obtained.

~~~bash
$ git clone https://github.com/projectlibra/projectlibra.git
~~~

- Once you clone the repository, you will encounter a file structure like the following:

~~~bash
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

~~~bash
$ cd libra-frontend
$ npm install
~~~

#### Setting up the HOST IP

You must change the host IP embedded in the file **host.js** for the backend server that you are running:

~~~bash
var host = 'Backend Server IP:PORT'
~~~

#### Runnning the client

You can run the client via npm and the landing page will be displayed in the default browser:

~~~bash
$ npm start
~~~

### Building the Server

Since the server has many dependencies in Python, we suggest using a virtual environment:

~~~bash
$ pip install virtualenv
$ virtualenv libra
$ source libra/bin/activate
# For deactivating virtualenv
$ deactivate
~~~

#### Installing dependencies

~~~bash
$ cd libra-backend
$ pip install -r requirements.txt
~~~

#### Setting up a PostgreSQL Server

We consult you to [PostgreSQL server setup tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04) from digitalocean.

After the setup, the configuration line under **app.py** has to be changed with the following information:

~~~
postgres://user_name:password@db_server_ip:port/db_name
~~~

#### Setting up SnpEff

We consult you to [SnpEff installation manual](http://snpeff.sourceforge.net/SnpEff_manual.html) 

In addition to the installation procedure, we need GRCh38.86 database.

~~~bash
$ java -jar snpEff.jar download -v GRCh38.86
~~~

#### Running the Server

The following will run the back-end server with the specified **PORT** on the server's IP address accepting all connections.

~~~bash
$ cd libra-backend
$ flask run --host 0.0.0.0 --port PORT
~~~
