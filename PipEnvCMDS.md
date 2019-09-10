# Pipenv Commands

```shell
# Install Python
sudo add-apt-repository ppa:jonathonf/python-3.6
sudo apt-get update
sudo apt-get install python3.6
```

```shell
# Create a folder djnago-handson
mkdir djnago-handson
```

```python
# Install Pipenv
pip install pipenv
```

```shell
# Move to the directory where you have create django-workshop folder
cd /home/rupesh/djnago-handson
```

```python
# Creates virtual environment using python 3.6
pipenv install --python 3.6
```

```python
# Activate pipenv virtual environment
pipenv shell
```

```python
# List all the python packages installed in the virtual environment
pip list
```

```python
# Install django in the virtual environment
pipenv install django==2.2
```  

```python
# Activate pipenv shell - activates the pipenv environment
pipenv shell
```

```python
# install package
pipenv install packageName
```

```python
# Uninstall package
pipenv uninstall packageName
pipenv clean                  # to clean the environment and remove the uninstall packages from environment
```

```python
# After pipinstall run piplock
pipenv lock
```

```python
# Get the pipenv python environment
pipenv run which python
pipenv --venv
```

```python
# Installs the packers specified in Pipenvfile
pipenv sync
```
