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


### Match Maker

Match maker contains facilities which are creating a patient with diagnosis and human phenotype ontology(HPO) terms, showing over all view for patients, detailed view for a patient,  getting gene ontology similarity from VCF annotation,  HPO traverser, automated similarity notification system, manual similarity notification system, similarity threshold configuration.

#### Create New Patient

To create a new patient click "My Project" button on the navigator. After that, press "Create New Patient" button. Fill "Patient Name" and "Diagnosis".  Type HPO Tags via search bar and select from dropdown menu. You can delete tags by pressing "Clean Tags" button. After adding all phenotypes, click "Create" button. 

#### See Overall View for Patients

Click "My Project" button on the navigator. Below of the  "Your Patient", you see all patients. For each patient you see patient name, patient id and patient diagnosis.

#### See Details for a Patient

On the overall view for patient, click detail button of correspondent patient. You will see same information with preview. Also you will see disease related phenotypes and affected gene names. If you click a phenotype, you can see details of phenotype and traverse on phenotypes. If you click gene name, you are redirected to gene information.

#### Editing a Patient

On the detailed Patient page, click "Edit Patient" button. You can give new name to the patient. You can change diagnosis via text box. You can add new phenotype via search bar. Also you can remove phenotypes by uncheck the checkbox of corresponded phenotype.

#### Get Highly Affected Genes For a Patient 

After uploading the vcf file, click patient logo. Select name of the patient. Automatically highly affected genes will be added to the patient.

#### HPO traverser

When you click phenotype name on the detailed patient page, you will be directed to the HPO traverser. On the traverser, you will see name of the phenotype, definition of the phenotype and relative phenotypes. You can traverse parents and children by clicking name of that phenotype. 

#### Automated Similarity Notification System

According to the threshold, if there is similar patient to the your patient, you will automatically get an e-mail which inform you about contact info of doctor who has similar patient. Also e-mail indicates both HPO similarity and GO similarity.  

#### Manual Similarity System

On  the detailed Patient page, click "Go Manual Matchmaker" link. There are three different system to use. Firstly, you can choose some phenotypes and search patient for that phenotypes and click "Run Manual Matchmaker" button. It returns proper patients for the query. Secondly, you can list patients which are most similar to the patient according to phenotype by clicking "Run HPO Matchmaker". Finally,  you can list patients which are most similar to the patient according to affected gene  by clicking "Run GO Matchmaker".

#### Similarity Threshold Configuration

Click "My Profile" button on the navigator. After that, enter value between 0 and 1 for both "Phenotype Similarity Threshold" and "Genotype Similarity Threshold". Click "Save Changes". New configuration affects Automated Similarity Notification System.

