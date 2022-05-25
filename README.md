## File-management-service

### Getting Started
---------------
Kindly follow below instructions for setting up your project locally. To get a local copy up and running follow these simple example steps.

### Prerequisites

- Install pyramid
```
    pip install pyramid
```

### Installation
- Clone the repo :
```
    https://github.com/Toorak-Capital/file-management-service.git
```

### Steps to be followed after cloning

- Change directory into your newly created project.
```
    cd filemanagement
```

- Create a Python virtual environment.
```
    python3 -m venv env
```

- Upgrade packaging tools.
```
    env/bin/pip install --upgrade pip setuptools
```

- Install the project in editable mode with its testing requirements. During this installation github will ask for authentication several times. Kindly provide authentication for the same.
```
    env/bin/pip install -e ".[testing]"
```


(Before moving to further steps kindly create a local database for the alembic commands to work. Also provide the path of the database in environment variables as "Database URL")


- Initialize and upgrade the database using Alembic.

    - Generate your first revision.
      ```
        env/bin/alembic -c development.ini revision --autogenerate -m "init"
      ```

    - Upgrade to that revision.
      ```
        env/bin/alembic -c development.ini upgrade head
      ```

- Load default data into the database using a script.
    ```
    env/bin/initialize_filemanagement_db development.ini
    ```

- Run your project's tests.
  ```
    env/bin/pytest
  ```

- Run your project.
  ```
    env/bin/pserve development.ini
  ```
