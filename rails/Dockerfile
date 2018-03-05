FROM ruby:2.5-slim
ENV LANG "C"
ENV LC_ALL en_US.UTF-8

# Install base dependencies
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev git-core postgresql-client gnupg curl imagemagick --no-install-recommends

# Install Node.js for asset management
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash && apt-get update -qq && apt-get install -y nodejs 

# Install Google Chrome
RUN curl -q https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
RUN apt-get update && apt-get install -y google-chrome-stable --no-install-recommends

# Install Yarn for asset packaging
RUN npm install -g yarn

# Add app code
RUN mkdir /usr/src/app
ADD . /usr/src/app
WORKDIR /usr/src/app

# Install dependencies
RUN bundle install

# Default command is to start a Puma server
CMD bundle exec rails server --binding=0.0.0.0
