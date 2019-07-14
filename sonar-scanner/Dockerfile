FROM openshift/jenkins-slave-base-centos7

USER root

ENV SONARQUBE_SCANNER_VERSION=3.2.0.1227 \
    PATH=$PATH:/sonarqube-scanner/bin \
    HOME=/home/jenkins \

WORKDIR /

# Install SonarQube Scanner
RUN set -x && \
    wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-$SONARQUBE_SCANNER_VERSION-linux.zip && \
    unzip sonar-scanner-cli-$SONARQUBE_SCANNER_VERSION-linux.zip && \
    rm sonar-scanner-cli-$SONARQUBE_SCANNER_VERSION-linux.zip && \
    mv /sonar-scanner-$SONARQUBE_SCANNER_VERSION-linux /sonarqube-scanner && \
    sed -i 's/use_embedded_jre=true/use_embedded_jre=false/g' /sonarqube-scanner/bin/sonar-scanner

CMD /bin/sh 
#CMD sonar-scanner