FROM ruby:2.7.1
WORKDIR /app

RUN apt-get update \
 && apt-get install -y \
    mariadb-client \
    less

COPY ./Gemfile ./
COPY ./Gemfile.lock ./
RUN bundle install
CMD wait 10; ./webapp/sql/init.sh; cd /app/webapp/ruby; bundle exec rackup --port 8000 --host 0.0.0.0
