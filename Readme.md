# Proyect with docker and xdebug installed to work as a template for future projects

## PHPStorm configuration

* Once we have the project configured we need to go to the IDE settings and in the PHP section we will configure the PHP language level. In this project it is 7.4.

* Then we will configure the CLI Interpreter by clicking the '...'. 
  * In the modal window we have to click in **+** and then the option which says **FROM docker, vagrant, etc**.
  It will open a new modal. 
    * This time we select the Docker Compose check, in server it should show Docker, if not click on the New button, to configure properly.
    
    * When that is done, on **Configuration files** go and select the docker-compose.yml in docker directory.
    
    * **Service** should be _php_ if not changed and **PHP interpreter path** _php_, set **Environment variables** with the `COMPOSE_PROJECT_NAME=symfonyxDebug` on **.env**
    
    * On **lifecycle** choose _Connect to existing container_.
    
    * In **General** section, it should detect our configuration. And nothing else has to be configured here. So click OK.

* Expand PHP and go to Debug. In Debug port set 9003 or the one you desire.

* Now we need to set our server, so in PHP > Servers add a new one
  * pointing to `localhost` as it figures in docker-compose.yml `PHP_IDE_CONFIG=serverName=localhost` 
  * with the port 8080 which is the one selected on the **.env**
  * select the check and look for the directory you choose to map as the working dir and configure it i.e: `full-path-to/docker-with-xdebug`  points to `/application` 

* In the principal view of the IDE click in the toolbar on **Add Configuration...** and then in **+**.
Here you will configure the test launch from the IDE. So select your scope in Test Runner and chose the objective of your test. In my case in Directory I will select the test folder, which doesn't exist yet in this project. Put the descriptive name you want. And select the Interpreter.


Start listening and put a breakpoint wherever you want. Now you will get the code inspected in that breakpoint
