FROM java:8-jre

ENV VERTICLE_FILE consumer-fat.jar

# Set vertx option
ENV VERTX_OPTIONS "-cluster"

# Set hazelcast options
ENV HAZELCAST_OPTIONS -Dhazelcast.max.no.heartbeat.seconds=10 -Dhazelcast.merge.first.run.delay.seconds=3 -Dhazelcast.merge.next.run.delay.seconds=3 -Dhazelcast.max.join.merge.target.seconds=5

# Set the location of the verticles
ENV VERTICLE_HOME /usr/verticles

# Copy your fat jar to the container
COPY ./verticles $VERTICLE_HOME

# Launch the verticle
WORKDIR $VERTICLE_HOME
ENTRYPOINT ["sh", "-c"]
CMD ["java $HAZELCAST_OPTIONS -jar $VERTICLE_FILE $VERTX_OPTIONS"]