# fagdag-continuousdelivery
Repo for fagdag Continuous Delivery

Oppsett

1) Gå til mappen /docker/ og bygg jenkinsroot-image  
docker build -t="jenkinsroot" .  

2) docker-compose up på docker-compose.yml i repository  
(NB: har man allokert mindre enn 4 GB minne til docker kan det medføre høy cpu-bruk (på osx i hvert fall)  

3) For å få tilgang til jenkins-container:  
docker exec -it jenkinsci bash  
bash-4.4# cd /var/jenkins_home/  

4) Lenker

Jenkins: http://localhost:8080/  
phpmyadmin: http://localhost:9080  
Mariadb: http://localhost:3306/  
SonarQube: http://localhost:9000

5) Følgende plugins kan være greit å installere i Jenkins

Plugin Slack Notification  
Pipeline utility steps  
SonarQube scanner  
AnsiColor  
FindBugs  
Pipeline Maven Integration  
Checkstyle  
PMD  
Flyway runner  
Task Scanner  
HTTP Request  
Locale  

6) Hvis jenkins har norsk tekst (og du ikke liker det)  
Sett locale til EN i Manage Jenkins -> Configure Systems  

7) Lesestoff  

https://jenkins.io/doc/book/pipeline/  
https://jenkins.io/doc/book/pipeline/syntax/  
https://jenkins.io/doc/pipeline/steps/  
https://jenkins.io/doc/book/pipeline/development/#pipeline-development-tools  
http://localhost:8080/job/<jobbnavn>/directive-generator/  




Intro: Jenkins tutorials

1) Maven-prosjekt  
https://jenkins.io/doc/tutorials/build-a-java-app-with-maven/  

2) Node/react webprosjekt  
https://jenkins.io/doc/tutorials/build-a-node-js-and-react-app-with-npm/  

3) Python-prosjekt (optional)  
https://jenkins.io/doc/tutorials/build-a-python-app-with-pyinstaller/  

4) Multibranch-prosjekt  
https://jenkins.io/doc/tutorials/build-a-multibranch-pipeline-project/  

5) Blue Ocean pipeline  
https://jenkins.io/doc/tutorials/create-a-pipeline-in-blue-ocean/  


## Notifications


Oppgave
Send en notification til Slack ved start og stopp av pipeline-eksekvering.

Legg på ulike properties i meldingene for å identifisere jobben.

Eksempler på tilgjengelige properties kan man finne her: http://localhost:8080/job/<jobbnavn>/pipeline-syntax/globals

Bruk forskjellige meldinger avhengig av status på bygget.

Info om slack-integrasjon: https://my.slack.com/services/new/jenkins-ci


## Health check
(krever HTTP Request plugin)

På slutten av en pipeline kan man kjøre en healthcheck mot applikasjonen for å se om den kom opp som den skulle.

Oppgave
Utvid controller med en health-check-metode som svarer ok/ikke ok på om systemet er oppe
Alternativt: simuler en healthcheck ved å f.eks gå mot et endepunkt her https://jsonplaceholder.typicode.com/

Oppgave
Legg inn et steg i pipeline som kjører mot healthcheck-endepunktet, og verifiserer at deploy gikk ok.
Bruk gjerne timeouts/retry i pipeline

