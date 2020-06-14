FROM ruby:2.7.0

RUN apt-get update -qq && \
  apt-get install -y --no-install-recommends mariadb-client-10.3

ENV APP_HOME /www/app
WORKDIR $APP_HOME

COPY Gemfile $APP_HOME
COPY Gemfile.lock $APP_HOME

RUN bundle install

ADD . $APP_HOME

COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]
