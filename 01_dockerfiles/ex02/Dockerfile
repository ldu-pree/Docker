FROM rails

RUN apt-get update -y &&  apt-get -y upgrade
RUN apt-get install -y nodejs
RUN gem update && gem install bundler && gem install rails 

COPY . /opt/app
WORKDIR /opt/app

ONBUILD RUN rails db:install
ONBUILD RUN rails db:create
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed

CMD ["rails", "s", "-b", "0.0.0.0"]

#docker build -t name .
#docker run -it --rm --name my-running-script -v "$PWD":/usr/src/myapp -w /usr/src/myapp name ruby script.rb