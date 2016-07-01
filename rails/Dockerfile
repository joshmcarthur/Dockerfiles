FROM ruby:2.2.4-slim
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev git-core postgresql-client nodejs nodejs-legacy npm --no-install-recommends
RUN npm install -g phantomjs-prebuilt
RUN mkdir /app
WORKDIR /tmp
ADD vendor/gem /tmp/vendor/gem
ADD Gemfile /tmp/Gemfile
ADD Gemfile.lock /tmp/Gemfile.lock
RUN bundle install
WORKDIR /app
CMD bundle exec rails server -b0.0.0.0
