# sample-python-app-flask

You need to:
- Create a repo in github for your app
- Create a webapp
- Inside webapp, Create a deployment using "Deployment center option to connect your app in github with your webapp
- Inside webapp, Change configuration to run your app. You need to add an environment variable in application settings
    FLASK_APP=hello:myapp
- Inside webapp, in general settings, change startup command to start your app in flask. In case you used default names for flask app you can avoid this step
    gunicorn --bind=0.0.0.0 --timeout 600 hello:myapp
- Check webapp
###
To configure dev environment in local for VSCODE
Use this tutorial: https://docs.microsoft.com/en-us/azure/developer/python/tutorial-deploy-app-service-on-linux-01
- Install python version 3.7
- Install Azure plugins in VSCODE
- sig in to azure in VSCODE
- Create a new folder, open it in VS Code, and add a file named hello.py with the contents below. The app object is purposely named myapp to demonstrate how the names are used in the startup command for the App Service, as you learn later.

    from flask import Flask
    myapp = Flask(__name__)

    @myapp.route("/")
    def hello():
        return "Hello Flask, on Azure App Service for Linux"

- In the same folder, create a file named requirements.txt with the following contents:
    Flask
- Open a terminal using the menu command Terminal > New Terminal.
- In the terminal, navigate to the folder containing hello.py. All the remaining terminal commands are run in this folder.
- Create and activate a virtual environment named .venv:
    # Assumes macOS/Linux
    sudo apt-get install python3-venv    # If needed
    python3 -m venv .venv
    source .venv/bin/activate

- When VS Code prompts you to activate the newly-created environment, answer Yes.
- Install the app's dependencies:
    pip install -r requirements.txt
- Set a FLASK_APP environment variable tells Flask where to find the app object:
    export FLASK_APP=hello:myapp
- Run the app:
    flask run
- Open the app in a browser using the URL http://127.0.0.1:5000/. You should see the message "Hello Flask, on Azure App Service for Linux."
- Stop the Flask server by pressing Ctrl+C in the terminal.
