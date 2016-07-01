FROM elixir:slim

RUN apt-get update &&\
    apt-get install -y curl &&\
    curl -sL https://deb.nodesource.com/setup_4.x | bash - &&\
    apt-get install -y nodejs &&\
    yes | mix do local.hex, archive.install https://github.com/phoenixframework/archives/raw/master/phoenix_new.ez, local.rebar

WORKDIR /app
CMD ["mix", "phoenix.start"]
