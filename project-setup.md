# Project Setup Steps (Development Mode)


### Prerequisites
* Ruby version: 2.5.0
* Rails version: 5.2.0
* Database Used: Postgres (for both development and production)
  * Set up postgres
    * Login to postgres and create a superuser  **(we need it because we're enabling a couple of extensions)**
      * `create role gdgapp with createdb superuser login password your-password;`   

### Setup the environment
* Open bash profile set the following
  * **GDG_APP_DEV_PASS** (development DB password)
  * **GDG_EMAIL_USERNAME**
  * **GDG_EMAIL_PASSWORD**
  * **GDG_GOOGLE_CLIENT_ID** (from Google console, enable Google+ API)
  * **GDG_GOOGLE_CLIENT_SECRET** (from Google console, enable Google+ API)



### Clone/Download
* `bundle install --deployment`
* `rails db:setup` (though this will load the seed as well, but you can run rake db:seed, just in case)
* `rails active_storage:install`
* `rails db:seed`
* Create an ER Diagram `rails db:migrate`

### Run the Server
* `rails s`
* Run: `gem pristine --all`


### Resque (for background jobs, mostly emails!)
* `QUEUE=* rake resque:work`




