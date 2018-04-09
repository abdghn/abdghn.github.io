#Hello World Flask

mkdir testFlask

cd testFlask

virtualenv my-first-env

source ./my-first-env/bin/activate

make file hello.py

FLASK_APP=hello.py flask run

open browser localhost:5000

#Jupyter Notebook with Virtualenv
cd venv/

source ./bin/activate

jupyter notebook
