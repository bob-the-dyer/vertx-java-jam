FROM java:8-jre

ENV SPRING_BOOT_FILE persistor-0.1.jar

# Set the location of the spring boot apps
ENV BOOTAPPS_HOME /usr/bootapps

# Set hazelcast options
ENV HAZELCAST_OPTIONS -Dhazelcast.max.no.heartbeat.seconds=10 -Dhazelcast.merge.first.run.delay.seconds=3 -Dhazelcast.merge.next.run.delay.seconds=3 -Dhazelcast.max.join.merge.target.seconds=5

# Copy your fat jar to the container
COPY ./bootapps $BOOTAPPS_HOME

# Launch the boot app
WORKDIR $BOOTAPPS_HOME
ENTRYPOINT ["sh", "-c"]
CMD ["java $HAZELCAST_OPTIONS $REMOTE_JMX_OPTIONS -jar $SPRING_BOOT_FILE"]