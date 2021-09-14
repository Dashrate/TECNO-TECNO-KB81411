# TECNO-TECNO-KB81411
FROM java:8

COPY . workdir/

WORKDIR workdir

RUN GRADLE_USER_HOME=cache ./gradlew buildDeb -x test

RUN dpkg -i ./gate-web/build/distributions/*.deb

CMD ["/opt/gate/bin/gate"]
