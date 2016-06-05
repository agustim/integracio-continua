# integracio-continua
Desenvolupmant un entornde integracio contiuna.

## Prerequists

La idea principal és crear un sistema robut de testing en un sistema de integracio continua.

Productes (de baix a dalt)
* [nightwatchjs](http://nightwatchjs.org/): Fer scripts de testing en javascript.
* [phantomjs](http://phantomjs.org/): Un browser per scripts.
* [SeleniumIDE ComplementF irefox](https://addons.mozilla.org/ca/firefox/addon/selenium-ide/): "Graba" session web.
* [Selenium-standalone](https://www.npmjs.com/package/selenium-server-standalone-jar): Modul npm amb una versió standalone.
* [SeleniumIDE to nightwatchjs](https://github.com/timjrobinson/seleniumide2nightwatch): Converteix scripts grabats amb seelniumIDE a nightwatch
* [Docker](https://docker.io): Crear containers
* [Docker-compos](https://docs.docker.com/compose/): Crear containers que es relacionen, necessitem la versio 2 (1.5 o superior)
* [Jenkins](https://jenkins.io/): Controlador i planificador de tests

## Altres
* [SonarQube](http://www.sonarqube.org/) : Controlador de qualitat del codi.

## Links interesnats
* https://blog.codecentric.de/en/2015/10/continuous-integration-platform-using-docker-container-jenkins-sonarqube-nexus-gitlab/
 * https://github.com/marcelbirkner/docker-ci-tool-stack
* https://blog.codecentric.de/en/2015/10/using-jenkins-job-dsl-for-job-lifecycle-management : Exemple d'us
* https://github.com/blueimp/nightwatch
* https://github.com/watarumohawk/nightwatchjs-e2e
* http://juristr.com/blog/2014/02/nightwatch-test-automation/

## Preparar

### Arrancar
```
docker-compose up
```

### Instal·lar Nodejs dintre del jenkins
```
docker exec -it ...jenkins /bin/bash
```
Dintre del container docker
```
apt update
apt install npm 
ln -s /usr/bin/nodejs /usr/bin/node
```
### Configurar una feina dintre del jenkins

Jenkins -> New Item -> Freestyle project  => posar un nom

Dintre de la "feina":
* Posar a build:
Execute shell
```
npm install
npm test
```
* Posar dintre de Add post-build action
Publish xUnit test results
```
test-reports.xml
```


