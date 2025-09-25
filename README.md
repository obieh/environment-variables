# Environment-Variables
## This project will show how to make ENVs available for development, testing and production environment respectively.

### Environment variables are key-value pairs configured outside your source code or script so that each value can change depending on the Environment(Development, Testing or Production Environments).

### Environment varaibles will differ for development, Testing and Production Environments respectively. 

* Environment variables for development might be 
```
 DB_URL=localhost
 DB_USER=test_user
 DB_PASS=test_pass
```

* Environment variables for testing might be:

```
 DB_URL=testing-db.example.com
 DB_USER=test_user
 DB_PASS=test_pass
```
* Environment variables for testing might be:

```
 DB_URL=production-db.example.com
 DB_USER=prod_user
 DB_PASS=prod_pass
```

### Why use environment variables?

* Security: Avoid storing sensitive data (like API keys, passwords) in the code.

* Flexibility: Configuration can change without altering the code (e.g., different settings for development, staging, production).

* Portability: Code can run in different environments without modification.

### How to use environment variables?

1. Setting environment variables:

    - In Unix-like systems (Linux, macOS): export VAR_NAME=value

    - In Windows: set VAR_NAME=value (for current session) or through system settings for permanent.

2. In scripts/code, you can access these variables.
#### Example in languages
```bash
#!/bin/bash
echo "Database host: $DB_HOST"
```

```python
import os
db_host = os.environ.get('DB_HOST')
# or with a default value
db_host = os.environ.get('DB_HOST', 'localhost')
```

```javascript
const dbHost = process.env.DB_HOST;
```

3. For development, you can use a .env file (not to be committed to version control) and a library to load it.

#### Best practices:
* Never commit .env files to version control.

* Provide a .env.example file with placeholder values (without secrets) to show the required structure.

* Use different .env files for different environments (if needed) and manage them securely.

### Demonstration:
1. Create a script file aws_cloud_manager.sh

![](./img/Pasted%20image.png)

2. paste the script below

```bash
#!/bin/bash

# Checking and acting on the environment variable
if [ "$ENVIRONMENT" == "local" ]; then
echo "Running script for Local Environment..."
# Commands for local environment
elif [ "$ENVIRONMENT" == "testing" ]; then
echo "Running script for Testing Environment..."
# Commands for testing environment
elif [ "$ENVIRONMENT" == "production" ]; then
echo "Running script for Production Environment..."
# Commands for production environment
else
echo "No environment specified or recognized."
exit 2
fi

``