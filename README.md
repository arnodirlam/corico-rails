# corico-rails
An example Rails project I use for teaching Database and Rails classes.

## Setup

Install [Git](http://git-scm.com/), if not installed yet.

### Ruby
Use RVM (Ruby Version Manager) to manage installed Ruby versions and Gemsets.
To install, follow the instructions on the [RVM website](https://rvm.io/).
If installed correctly, switching to the project path in a terminal (`cd .` if you're already in the project) should switch the local environment to the correct Ruby version and Gemset, specified in the project's .ruby-version and .ruby-gemset files, respectively.
The first time you enter, RVM should display that the Ruby version is not installed and instruct how to install it. Do that as well.
Then, install the gems specified in the Gemfile: `bundle install`

At the time of writing, these are the steps all together:
```
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
\curl -sSL https://get.rvm.io | bash -s stable
rvm install ruby-2.1-head
cd .
bundle install
```

### PostgreSQL
* Install [PostgreSQL](http://www.postgresql.org/), if not installed yet.
* Create user **corico** with password **soundslikeveggie** (see below for instructions).
    * superuser rights are needed to create databases (recommended for development).
* Create the database: `rake db:create`
* Run migrations: `rake db:migrate`
* Recommended: Also install [pgAdmin](http://www.pgadmin.org/), an UI for PostgreSQL servers.

#### On Ubuntu
```
sudo apt-get install postgresql pgadmin3 -y
sudo -u postgres createuser --superuser corico
sudo -u postgres psql
  -> \password corico
  -> soundslikeaveggie
  -> soundslikeaveggie
  -> \q
```

### Redis
#### On OS X
```
brew install redis
```

#### On Ubuntu
```
sudo apt-add-repository https://launchpad.net/~rwky/+archive/redis
sudo apt-get install redis-server -y
```

### MongoDB
#### On OS X
Refer to: http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/

#### On Ubuntu
Refer to: http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/

## Defaults
Admin login:
* `admin@example.com`
* `password`

## Workflow
### Develop
To pull code from Git, make sure to perform the following commands together:
```
git pull
bundle install
rake db:migrate
```
