FROM rabbitmq:management

# Define environment variables.
ENV RABBITMQ_USER event-platform
ENV RABBITMQ_PASSWORD opensource_at_123
ENV RABBITMQ_PID_FILE /var/lib/rabbitmq/mnesia/rabbitmq

ADD rabbitmq_delayed_message_exchange-3.9.0.ez /plugins/

ADD init.sh /init.sh
RUN chmod +x /init.sh
#EXPOSE 15672
RUN rabbitmq-plugins enable --offline rabbitmq_delayed_message_exchange
RUN rabbitmq-plugins enable rabbitmq_management

# Declare the delayed message exchange
RUN apt-get update
RUN apt-get install -y curl
ADD delayed_exchange.json /delayed_exchange.json

# Define default command
CMD ["/init.sh"]
