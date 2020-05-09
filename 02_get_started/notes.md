## Create a new Rails project

`rails new`
Generate a new Rails application

`bundle exec rails new -h`
Have a look at the options

## Examine the file structure of a RoR project

- Use the app previously generated
- Explain what goes in which folder

## Configure a RoR project

- we usally don't touch application.rb - well documented - just as all Rails config files
- initializers folder - all files run right at application boot
- environments folder
  - introduce .yml files
  - talk about different environments
- log into mysql

`mysql -uroot -p`
`CREATE USER 'rails_user'@'localhost' IDENTIFIED BY 'password';`
`GRANT ALL PRIVILEGES ON * . * TO 'rails_user'@'localhost';`
`FLUSH PRIVILEGES;`
`mysql -urails_user -p`

- database.yml - set up according to previous step

## Access running application from a browser

`bundle exec rails server`
  or
`bundle exec rails s`

`bundle exec rails server -h`

ctrl+C to stop it

Open the application in browser

## Generate a controller and a view

List generate command options:
`bundle exec rails generate`

`bundle exec rails generate controller Demo index`
`bundle exec rails generate c Demo index`

- show the created controller
- show the created views
- show the created route
- we could have done this by hand - generators are just making it simpler

## Examine how server requests are handled
TODO: add the screenshot here

- Add a `static.html` file to public folder
- Show in web browser that it shows up
- Move this to the 'demo' folder
- Show in web browser that it shows up now in demo/static.html or demo/static (!no .html extension necessary)
- change its name to index.html - our controller action is not accessible any more!

## Defines routes in a RoR project

No static file found in public folder -> routing parses url

Examine `routes.rb` file

Route types:
- simple match route
  get 'demo/index'
- default route
  get ':controller(/:action(/:id))'
- root route
  root 'demo#index'
- resourcful root

## Challenge: Experiment

- generate at least one more controller - with the generator and manually
- try creating more views
- write several routes
- add some static files
