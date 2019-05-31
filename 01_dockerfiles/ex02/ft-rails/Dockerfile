# From the docker page for rails
#	https://docs.docker.com/compose/rails/

#	FROM ruby:2.5
#	RUN apt-get update -qq && apt-get install -y nodejs postgresql-client
#	RUN mkdir /myapp
#	WORKDIR /myapp
#	COPY Gemfile /myapp/Gemfile
#	COPY Gemfile.lock /myapp/Gemfile.lock
#	RUN bundle install
#	COPY . /myapp
#	
#	# Add a script to be executed every time the container starts.
#	COPY entrypoint.sh /usr/bin/
#	RUN chmod +x /usr/bin/entrypoint.sh
#	ENTRYPOINT ["entrypoint.sh"]
#	EXPOSE 3000
#	
#	# Start the main process.
#	CMD ["rails", "server", "-b", "0.0.0.0"]

# FROM ruby:2.5
# RUN apt-get update && apt-get install -y nodejs postgresql-client && \
#	gem install 'rails' 'bundler:~>1.3.0' && \
#	mkdir -p /opt/app
# RUN apt-get update -y && apt-get install -y build-essential libpq-dev nodejs sqlite3
# build a new rails app
# ONBUILD COPY app /opt/app
# ONBUILD WORKDIR /opt/app
# ONBUILD RUN bundle install
# rails generate [option][args]
# so rails generate [migration][migration name] column:datatype [...]
# rake is a DSL (domain specific language // only works for ruby)
# from what i understand t is basically 'make' but for ruby
# ONBUILD RUN rake db:migrate
# ONBUILD RUN rake db:seed

FROM ruby

RUN apt-get update -y && apt-get upgrade -y && \
	apt-get install nodejs -y && gem install rails bundler

ONBUILD WORKDIR /opt
ONBUILD RUN rails new app
ONBUILD WORKDIR /opt/app
ONBUILD RUN bundle install
ONBUILD RUN rails generate migration FunName name:string
ONBUILD RUN rake db:migrate
#docker build -f ft-rails/Dockerfile -t ft-rails
#docker tag ft-rails:latest ft-rails:on-build
#docker build -t ex02 .
#docker run --rm -it --name ft-rails -p 3000:3000 ex02
