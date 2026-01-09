FROM eclipse-temurin:21-jdk-alpine AS build

ARG DEPENDENCY_CHECK_VERSION=12.2.0

RUN "$JAVA_HOME/bin/jlink" \
        --compress=zip-6 \
        --module-path /opt/java/openjdk/jmods \
        --add-modules java.base,java.compiler,java.datatransfer,jdk.crypto.ec,java.desktop,java.instrument,java.logging,java.management,java.naming,java.rmi,java.scripting,java.security.sasl,java.sql,java.transaction.xa,java.xml,jdk.unsupported \
        --output /jdk

RUN    apk add --no-cache --virtual .build-deps curl \
    && curl -Ls https://github.com/dependency-check/DependencyCheck/releases/download/v${DEPENDENCY_CHECK_VERSION}/dependency-check-${DEPENDENCY_CHECK_VERSION}-release.zip -o /tmp/dependency-check.zip \
    && unzip /tmp/dependency-check.zip -d /usr/share \
    && rm /tmp/dependency-check.zip

FROM alpine

COPY --from=build /jdk /opt/jdk/
COPY --from=build /usr/share/dependency-check /usr/share/dependency-check

ENV JAVA_HOME=/opt/jdk
ENV PATH="$PATH:/usr/share/dependency-check/bin"

ADD ./data /usr/share/dependency-check/data

# The data folder itself must be writable by anyone because an update lock needs to be written there.
# Without these permissions any attempt to call dependency-check.sh as anyone other than root will simply hang.
# Adding --chmod=0777 to the ADD command does the inverse of what we want; it sets the permissions to all files inside the data folder but not the data folder itself.
RUN chmod go+w /usr/share/dependency-check/data

ENTRYPOINT ["/usr/share/dependency-check/bin/dependency-check.sh"]
