from python:3.6

RUN apt-get update
RUN apt-get install -y nginx

# flask動かすため
RUN pip install uwsgi
RUN pip install flask line-bot-sdk

# nginxの設定
COPY default /etc/nginx/conf.d/bot.conf
RUN rm /etc/nginx/sites-available/default
RUN rm /etc/nginx/sites-enabled/default

# その他設定
COPY start.sh /
COPY uwsgi.ini /

CMD ["sh", "/start.sh"]
