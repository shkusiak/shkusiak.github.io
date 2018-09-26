---
layout: post
title:      "Exploring the Long Tail of Shoes "
date:       2018-09-26 12:14:18 -0400
permalink:  exploring_the_long_tail_of_shoes
---

# Exploring the Long Tail of Shoes
> > “A best-seller and a neverseller are just two entries in a database; equal in the eyes of technology and the economics of storage.” ― Chris Anderson, The Long Tail: Why the Future Is Selling Less of More

The above quote speaks to me. Two books are entered into a database of books through a CRUD app. They each have attributes: title, author, cost, genre, summary, rating, reviews, etc. They each have roughly the same word count and when printed are similar in dimensions and weight. How do I as a user know which one to buy? Ratings and reviews? Not always... 

Everyone loves shoes, that's easy. But I'm sick of the one's I've got. I'm sick of the ones I keep seeing on the streets and I'm sick of the recommendations I keep getting through whatever algorithims I am analyzed by. I want to open my eyes to the world of shoes beyond what is mainstream. I want to take a deep dive into the internet and get a recommendation from myself in an alternate universe, only just a step ahead of me. This morning a saw a girl on the subway with a pair of worn out tassel loafers in a perfect burgundy. Where'd she get them? I bet she has a pair of equally 'cool' sneakers that I'd be into. If only I could follow her...

For this porfolio project I created a sinatra app to catelog users and their shoe collection. The goal of this application would be to connect users to one another based on the shoes in their collection and other peoples shoes that they like. Hopefully with enough users and enough data, this will expose users to the long tail of shoes. 

# App Creation Process
My app is written in Sinatra/ActiveRecord and uses a MVC (model, view, controller) pattern. I started the process by creating the environment I wanted the app to live in. I created a repo on Github and used passed similar projects to create Rakefile, Gemfile, config.ru and Config>environment.rb files, while recongnizing that I knew I would need to use `tux`, `ActiveRecord`, `rake`, `shotgun`, `pry`, `sinatra`, and `capybara`.

The next step was to create a db folder for the database. Before creating the files, I tried stubing out the objects I wanted to create on paper, and mapping out the relationship I wanted them to have. I decided I wanted two models: users and shoes with relationships of `belongs_to` and `has_many`. In order to make the databases I created two migrations for :users and :shoes.  To make the tables I used `rake db:create_migration NAME="create_users"`. The users each have attributes username, email & password, while the shoes have name, manufacturer, description, color and cost. 

**Hint:** Don't forget to make sure the model with the `belongs_to` relationship also has an  `t.integer :user_id` attribute! I learned that the hard way... Once the columns were identified I ran `rake db:migrate` to get the database set up.

After the DB was set up, I started to map out the models, views, and controllers within my app folder. The models were quick and easy to write because they were just to match the db I set up. So, next I started by thinking about which pages or views the user should see. Index, signup, login, shoes, create_shoe, edit_shoe, shoe/:id and then a layout page to show information that will be on all pages. One page I forgot about until the end was a page to show only one users shoes.

The next step was to stub out my controllers: ApplicationController, UsersController and ShoesController. In my ApplicationController I have the below code in order to allow for password encrption. I also have two helper methods so I can frequently test if user is #logged_in? and pull info from the #current_user.

```
  configure do
    set :public_folder, 'public'
    set :views, 'app/views'
    enable :sessions
    set :session_secret, "password_security"
  end
```

My UsersController has your basic get and post requests for signup, login, and logout. It also has a get request to show a page with all of 1 users shoes. The special thing about my UsersController was validating usernames and email addresses. I did this by creating messages like this `session[:message] = "Email already exists, login or try again."`, redirecting to the same page and printing the message in the view. Make sure to include `register Sinatra::ActiveRecordExtension` at the top of your UsersController for this to work.

My ShoesController has your basic get, post, patch, and delete requests for shoes to be made, edited and deleted. The key to here was making sure all the links were right and each `redirect` was working properly. Testing the app through `shotgun` helped me with this process.

**Hint:** Don't forget to mount your new controllers in config.ru!

```
use Rack::MethodOverride
use UsersController
use ShoesController
run ApplicationController
```

**Comments/Hints/Struggles:**
1. Creating the db right the first time around, so you don't have to rollback or create modification migrations after the fact.  I had a few typos in my original migration which I realized waaaay late. 
2. Validating usernames & email addresses - I used session[:message] to alert the user if a username or email adress was already associated with an account.
3. Time management - always an issue, as I have a full time job
4. I went on a 2 week vacation in the middle of this app creation which made the process wayyy longer than it needed to be.

My app can be found [here](https://github.com/shkusiak/sinatra_app).

