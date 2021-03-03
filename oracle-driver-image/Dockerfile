FROM registry.redhat.io/rhpam-7/rhpam-kieserver-rhel8:7.8.1

LABEL  "io.openshift.build.image"="registry.redhat.io/rhpam-7/rhpam-kieserver-rhel8" \
       "io.openshift.build.source-location"="/tmp/build/inputs" \
       "io.openshift.s2i.destination"="/tmp" \
        name="Oracle JDBC Driver" \
        version="12.2.0.1"

# Provide the right value during build

ENV CUSTOM_INSTALL_DIRECTORIES="extensions/*"

USER root
# Copying provided install.sh install.properties and modules to /tmp/src/extensions/extras/
COPY install.sh oracle-driver-image/install.properties /tmp/src/extensions/extras/

COPY oracle-driver-image/modules /tmp/src/extensions/extras/modules/
# Copying the driver jar inside the module folder
COPY oracle-driver-image/ojdbc8.jar /tmp/src/extensions/extras/modules/system/layers/openshift/com/oracle/main/ojdbc8.jar

RUN chown -R 185:0 /tmp/src

USER 185
# Running s2i assemble
RUN /usr/local/s2i/assemble

# Run user
USER 185

# Specify the working directory
WORKDIR /home/jboss

# Specify run cmd
CMD /usr/local/s2i/run



