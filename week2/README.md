#  Quick Tutorial/References

## Cloud Foundry

### 1. Account Setup

- Go to [Pivotal](https://www.pivotal.io) and create a new account.
- Based on your OS, download **CLI**
    - [Windows](https://cli.run.pivotal.io/stable?release=windows64&source=github)
    - [Linux](https://cli.run.pivotal.io/stable?release=debian64&source=github)
    - [Other versions](https://github.com/cloudfoundry/cli#downloads)

- On the CLI, type

        $ cf help

### 2. Make your app

- Navigate to the app directory:

        $ cd <app_name>

- Sign in to PWS:

        $ cf login -a https://api.run.pivotal.io 
        
- Push the app to PWS:

        $ cf push

- In case of any `errors` you can type:

        $ cf logs <app_name> --recent

### 3. Make your *config* files.
You have to make three files:

- **Procfile**

        web: python test.py

- **requirements.txt**

        Flask

- **test.py**
 
        from flask import Flask
        import os
        app = Flask(__name__)
        port = int(os.getenv("PORT"))
        @app.route('/')
        def hello_world():
            return 'Welcome'
        if __name__ == '__main__':
            app.run(host='0.0.0.0',port=port)


