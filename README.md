## CI-CD on GCP
Step1: Enable Google APIs to activate the service
```ruby
gcloud services enable container.googleapis.com
```
Step 2: Create repository on google cloud source repository
```ruby
gcloud source repos create hello-YOUTUBE
```
Step 3: Clone the repository
```ruby
gcloud source repos clone hello-YOUTUBE
```
Step 4: Change directory and make 2 files and push to cloud source repo
```ruby
cd hello-YOUTUBE/
```
**Create app file**
```ruby
nano main.py
```
**Create deployment yaml file**
```ruby
nano app.yaml
```
**Commit and push the files to cloud source repo**
```ruby
git add .
```
**Before commiting check configuration of username and email** 
```ruby
git commit -m "Add app to cloud source repo"
```
**Push to master**
```ruby
git push origin master
```
Step 5: Deploy the application using app.yaml
```ruby
gcloud app deploy app.yaml
```
**Get URL of the deployed instance**
```ruby
gcloud app browse
```
Step 6: Add cloudbuild.yaml and push changes
```ruby
nano cloudbuild.yaml
```
**Commit message**
```ruby
git commit -m "Add cloudbuild yaml"
```
Step 7: Go to cloud build product and click on dashboard. Click on set up build
trigger. Give the name to trigger (app-eng-build-trigger). Select repository
under source and select configuration as cloud build configuration
(yaml or json). Then click on Create to create Trigger.<br>
**Enable permissions**<br>
Step 8: Within cloud build Go to settings and Enable **App Engine Admin**. If it 
asks to enable Google API then enable it. Also enable **Service Account**<br>
Step 9: Make changes in main.py and then commit and push to cloud source repo<br>
**Commit message**
```ruby
git commit -m "Add new youtube change"
```
