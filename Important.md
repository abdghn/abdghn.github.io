#Hello World Flask

mkdir testFlask

cd testFlask

virtualenv my-first-env

cd


 source my-env/bin/activate


 . my-env/bin/activate

make file hello.py

FLASK_APP=hello.py flask run

open browser localhost:5000

#Jupyter Notebook with Virtualenv
cd venv/

source ./bin/activate

jupyter notebook
