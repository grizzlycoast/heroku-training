This is a training repo to produce a PHP sample app, with api integrations, and other desired tools/services (S3/bucketeer, PGSQL add-on, Browserstack automated QA). 

Heroku Flow

Create Pipeline For Git Repository
1.	Login to Heroku

2.	In top left, click on “Personal apps”
a.	Select “grizzlycoastmedia” (note this may already be selected)

3.	Create Production App and Add to Pipeline
a.	Click on “Apps”

b.	In top right, click “New”
i.	Select “Create new app”

c.	Type in app name (optional, but easier to find app afterward). 
i.	Example: “lumavieskincare” for “lumavieskincare.com”

d.	Click “Create App”

e.	Click on “New Pipeline”

f.	Click on “Create Pipeline” (name if needed)
i.	Example: “lumavieskincare” for “lumavieskincare.com”

4.	Create Stage App and Add to Pipeline
a.	Click on “grizzlycoastmedia” in top left

b.	Click on “Apps”

c.	In top right, click “New”
i.	Select “Create new app”

d.	Type in app name (optional, but easier to find app afterward). 
i.	Example: “stage-lumavieskincare” for “lumavieskincare.com”

e.	Click “Create App”

f.	Click on “grizzlycoastmedia” in top left

g.	Click on “Apps”

h.	Click on production app
i.	In this case it would be “lumavieskincare”

i.	Click on the pipeline for this app (multiple app icon next to “grizzlycoastmedia” in top left

j.	Click “Add app” next to “staging”


k.	Type in stage app name and select it
i.	In this case it would be “stage-lumavieskincare”

5.	Connect to GitHub:
a.	From the pipeline for these apps, select the production app
i.	In this case “lumavieskincare”

b.	Click “Deploy”

c.	Beside “Deployment method”, click “GitHub Connect to GitHub”

d.	Beside “Connect to GitHub”, select “grizzlycoastmedia” from the dropdown

e.	Type in repository name and click “Search”

f.	Beside the correct repository, click “Connect”

g.	Beside “Automatic deploys”, click “Enable Automatic Deploys”

6.	Add Review to Pipeline
a.	From the pipeline for these apps, there should now be a “Review Apps” section. 

b.	Click “Enable Review Apps…”

c.	Click “Create an app.json File…”


d.	Scroll down new page and click “Commit to Repo”

e.	Click on “Create new review apps for new pull requests automatically” checkbox


f.	Click “Enable”


7.	Tell Heroku how to use this app
a.	For php, add an composer.json file with only these braces “{}” in the file to repository root directory
b.	For php, if there isn’t an index file in root, add Procfile to repository root directory telling it where the entry point is
i.	web: vendor/bin/heroku-php-apache2 public_html/

Adding Work to Existing Pipeline
1.	Create Git branch off master:
git checkout -b {yourBranchName}
2.	Create remote git branch for pushing:
git push –set-upstream origin {yourBranchName}
3.	Create Heroku app for branch:
		heroku create

4.	Push code to Heroku app:
git push heroku {yourBranchName}:master
5.	You can now view the page:
heroku open
6.	Make changes to branch and commit/push to git for version control, as well as heroku app to view changes.

7.	Task is ready for dev QA using the link from “heroku open” command

8.	When the task is finished QA, go to github and select the repository

9.	Click on {yourBranchName}

10.	Click on “Compare & pull request”

11.	Check changes are as expected and click “Create pull request”

12.	Once review/testing is finished, move app to either stage or production by clicking the dropdown on the app and selecting “Move app to {environment}”
