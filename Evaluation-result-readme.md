## Evaluation-result service

### About the service

This service test evaluation results and gives output as pass / fail. To Retrieve Results, Results need to be populated based on result type (Calculated, Overwritten) then using coalesce command, relevant result value can be retrieved(With priority for Overwritten value).
Also we can retrive result type, individual result group and update grades using this service.
<br />
<br />


The below link provides overall Architecture of the service:<br />
[Evaluation-result service](https://toorakcapital.atlassian.net/wiki/spaces/PA/pages/234586413/Evaluation+Results)


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

<br />
(Before moving to further steps kindly create a local database for the alembic commands to work. Also provide the path of the database in environment variables as      "Database_URL". The format for DATABASE_URL is : 'postgresql://username:password@localhost:port/databasename'. <br />  
 Example : postgresql://postgres:pass123@localhost:5432/code-test )
<br />
<br />

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

**_NOTE:_**  The above commands are applicable for Mac. For windows one will have to replace 'bin' with 'Scripts'.<br /> 
Example- env/Scripts/pserve development.ini
