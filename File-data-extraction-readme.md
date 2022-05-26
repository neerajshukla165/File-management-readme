## File-data-extraction Service

### About the service

As the name suggests, this service extracts data from different excel file attached to the platform. It extracts different tables such as data mapper(Name of the key to which data from excel will be mapped), header pos(Eg:Property Location, Property Valuation), excel_sheet (Name of the worksheet in excel), etc. <br />
<br />

The below link provides overall Architecture of the service:<br />
[File-data-extraction Service](https://toorakcapital.atlassian.net/wiki/spaces/PA/pages/216236033/Data+Extraction+Service)


### Getting Started
---------------
Kindly follow below instructions for setting up your project locally. To get a local copy up and running follow these simple example steps.

### Prerequisites

- Install pyramid
```
    pip install pyramid
```

### Environment Setup

- AWS_ACCESS_KEY_ID 
- AWS_DEFAULT_REGION <br />
- AWS_SECRET_ACCESS_KEY <br />
- BUCKET_NAME <br />
- TOPIC_ARN <br />


### Installation
- Clone the repo :
```
    https://github.com/Toorak-Capital/file-data-extraction-service.git
```

### Steps to be followed after cloning

- Change directory into your newly created project.
```
    cd data_extraction
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
 Example : postgresql://postgres:pass123@localhost:5432/file-data-extraction )
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
    env/bin/initialize_data_extraction_db development.ini
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
