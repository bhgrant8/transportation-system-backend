# Hack Oregon Transportation Systems Backend Repository

This repo represents the work of the Transportation Systems project of Hack Oregon. We are a volunteer project for Open Data.

This repo is intended to be run in a docker environment.

## Getting Started

In order to run this you will want to:

1. Clone this Repository
2. `cd` into it
3. copy the `/bin/env.sample` file to create a `.env` file in same directory:
```
$ cp ./bin/env.sample ./bin/.env
```
4. open the `./bin/.env` in your text editor and complete the environmental variables. When working in your dev. environment, only the prefilled ones really matter. If you are working as part of the project team we will discuss any need for standardization or other environments in team setting.

Annotated sample:

```
PROJECT_NAME=<This will be our canonical project name once it is figured out>
DEBUG=True - <Switch to go from dev server environment to prod>
API_DOCKER_IMAGE= <what you want to name the local docker image for api>
POSTGRES_DOCKER_IMAGE= <what you want to name the local docker image for POSTGRES>
POSTGRES_USER= <User in postgres environment>
POSTGRES_NAME=odot_crash_data <Database name in postgres environment set to odot_crash_data for current dataset>
POSTGRES_HOST=db <connects to database container name in the docker compose file>
POSTGRES_PORT= <port for the database>
POSTGRES_PASSWORD= <password, make it strong and unique>
DJANGO_SECRET_KEY= <a secret key also should be long, unique random string>
```

5. Currently when working with the odot_crash_data, you will need to download the sql from the team drive and save into the bin folder: `./bin/odot_crash_data.sql`

6. Both of the above files are already added to the `.gitignore` file. Provided you do not rename them or change locations they should not be committed to the repo and this project should build and run.

7. Confirm you have executable perms on all the scripts in the `./bin` folder: `$ chmod +x ./bin/*.sh` Feel free to read each one and assign perms individually, cause it is your computer :stuck_out_tongue_winking_eye: and security is a real thing.

8. Run the `build.sh` script to build the project. Since you are going to be running it on the local machine you will want to run: `./bin/build.sh -l` - This command is doing a docker-compose build in the background. It is downloading the images needed for the project to your local machine.

9. Once this completes you will now want to start up the project. We will use the start.sh script for this, again using the `-l` flag to run locally:  `./bin/start.sh -l` The first time you run this you should see a bunch of sql commands running and will probably see the api container give an error about the database not being available on the port you set. Don't worry, just wait for the startup to finish. (Though this is not an ideal process it works for now).

10. Once the first startup completes kill the container using cmd c/ctrl c depending on your os.

11. Restart the container using the same start command:  `./bin/start.sh -l` and both the db and the api should startup.

12. Open your browser and you should be able to access the Django Restframework browserable front end at: http://localhost:8000/api and Swagger at http://localhost:8000/schema

13. To Run Tests: run the `./bin/build-test.sh -l` command.


## Contributing

To develop on the repo,

1. Create an issue for tracking and communication

2. You will clone repo and then create a feature branch.

3. After branching confirm you can follow above get started steps.

4. Develop you feature

5. Update documentation and env sample file as necessary.

6. Commit Changes.

7. Merge current Staging branch into feature branch to resolve any merge conflicts.

8. Push local feature branch to Hack Oregon repo. Any PR requests from forks will be rejected.

9. Create a Pull Request to staging branch. No PRs will be accepted to Master unless from staging and by approved reviewers

10. PR should be reviewed by authorized reviewer, another team member if possible, and pass any automated testing requirements.

11. Any outstanding merge conflicts resolved

12. Authorized reviewer will commit to staging.

13. Process for staging to master will be defined.

## License

We follow the MIT License: https://github.com/hackoregon/transportation-system-backend/blob/staging/LICENSE

## Contributors

<To Be added>