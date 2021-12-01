# Auto app deployment using Flask, Git and Heroku



## Install Heroku and Git

[Source for Heroku](https://devcenter.heroku.com/categories/python-support)
[Source for Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
[First time Git setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)


After installing Heroku and Git, and creating an account on Heroku, use the command line and login on Heroku to see if everything works correcly:

```
$ heroku login
```

Copy the path of your local Python app and clone the directory. In my case:
```
cd C:\Users\annas\PycharmProjects\lab3
```
## Create the app

Go to Heroku website (heroku.com), login and create a new App; choose a meaningful name for your App. 

## Add Procfile & requirements.txt

### Procfile setup
Open your project in your favourite code Editor or Navigate to your project directory and create a file named Procfile. It needs to have no extension. Next, using any code editor like VSCode or TextEdit, open the Procfile, and replace any text already prevalent with:

```
web: gunicorn app:app
```
### Requirements.txt setup
The requirements.txt file makes it easier for Heroku to install the correct versions of the required Python libraries (or “packages”) to run your Python code.

We are going to tell Heroku packages to install using our requirements.txt: open your project folder on your Command Line Interface (CLI) inside your environment use the following command:
```
 $ pip freeze> requirements.txt
```
this should automatically generate a requirements.txt file for you with all dependencies and libraries used in your App listed in the file.

Warning: always check the requirements. If you have too many installed, this may create problems. In this cases, it is useful to consider using the library ```pipreqs``` to generate them.

## Deploying to Heroku

Now, it is time to deploy our python bot or script to Heroku.

To do this, Open Your project folder On your Command Line Interface (CLI) inside your environment use the following command:
```
heroku login
heroku git:remote -a NAME_OF_YOUR_HEROKU_APP
git add .
git commit -m "Deployment commit"
git push heroku master 
```
Where:
- Heroku login logins into your Heroku account
- ```heroku git:remote -a NAME_OF_YOUR_HEROKU_APP``` is an Heroku shortcut to link a folder with an existing Heroku app;
- Git commit records changes to the repository
- Git push is used to upload local repository content to a remote repository. Pushing is how you transfer commits from your local repository to a remote repo.

## Why doesn't it work?
If something is not working, use Heroku logs:

Real-time tail displays recent logs and leaves the session open for real-time logs to stream in. By viewing a live stream of logs from your app, you can gain insight into the behavior of your live application and debug current problems. When you are done, press Ctrl+C to return to the prompt.
```
$ heroku logs --tail
```
When the error is caused by something in your app, though, use the filter of app logs:

```
$ heroku logs --source app
```
There are [other types of logs](https://devcenter.heroku.com/articles/logging).

## I'm on my own and it doesn't work. What can I do?
Besides writing to me, there are more than one ways to find help online:
1. You can ask a question or look for similar questions on [StackOverflow](https://stackoverflow.com/)
2. You can ask a question or look for similar questions on relevant subreddits of [Reddit](https://www.reddit.com/r/Heroku/)
3. Sometimes, but quite rarely, the problem is with platforms/frameworks themselves. In this case, you can open a Github issue or look on other open/closed issues on the relevant Github repository, for example [the Flask one](https://github.com/pallets/flask/issues).

## Notes
- There are other ways of deploying an application on Heroku. For instance, it is possible to put all the files on Github and do the deployment on the Heroku online dashboard. Likewise, it is possible to do everything without touching the Heroku dashboard. This example is an intermediate way between the two;
- Heroku is not a free application. This means you get up to five apps for each account;
- You can make changes to your files, of course, but it's important that you always commit the changes you made and push them again;
- If feel like you need to know more about Git, [this is a useful resource](https://www.atlassian.com/git/tutorials/setting-up-a-repository)
- Sometimes Heroku doesn't accept certain versions of Python or certain versions of libraries. This is why you should always read the documentation and make changes based on what is currently supported.


