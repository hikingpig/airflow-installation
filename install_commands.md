* for ubuntu 20.04, python3.8 is too old to install `airflow` correctly.

-> must install python3.10

# install python3.10
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
* view the packages'list

sudo apt list | grep python3.10
sudo apt install python3.10 python3.10-venv python3.10-dev python3.10-distutils

# add pip3.10 to PATH
* pip3.10 is already in ~/.local/bin. add this line to ~/.bashrc

export PATH=$PATH:$HOME/.local/bin:
* if HOME is not set, set it to your home folder

# create venv
python3.10 -m venv airflow_test1

source airflow_test1/bin/activate

# install apache-airflow
python -m pip install apache-airflow

# init airflow
airflow db init
airflow users create --username admin --password admin --firstname Anonymous --lastname Admin --role Admin --email admin@example.org 

# check webserver and scheduler
airflow webserver
* (in another terminal with same venv)

airflow scheduler
