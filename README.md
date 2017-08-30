# Java CI/CD App Boilerplate

This app is created by the standard Maven Webapp archetype with Spring REST support added. 

AWS distribution support according to the Continuous Integration/Delivery principle using Docker.

## Runtime Requirements

- JDK 1.8
- Maven 3.X
- Tomcat 7+

## Testing

Supports both Unit and Integration Tests using Maven Surefire and Failsafe plugins.

- `mvn verify` - Runs all tests

### Run Unit Tests

All unit tests are located in the directory `src/test/java` and do not need any further setup. 
- `mvn test` - Runs the unit tests

### Run Integration Tests
This app uses [Selenium](http://www.seleniumhq.org) for API client testing over Http which requires a WebDriver to be downloaded. The default driver is set to be the [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/downloads).

Next, you have to enter the path to your recently downloaded driver in the environment variable `SELENIUM_WEBDRIVER_PATH`.

Following commands will trigger the tests 
- `mvn integration-test` - Runs the integration tests in directory `src/integration-test/java`

## Eclipse IDE Support
- `mvn eclipse:eclipse` - Adds Eclipse Dynamic Web support

## Build and run with Docker

First build and package the project with maven

`docker run -it --rm -v "$PWD":/app -w /app maven:3.3-jdk-8 mvn clean package`

Build your image

`docker build --rm=false -t aws-java-app .`

Run the recently built image

`docker run --rm -p 8080:8080 aws-java-app`

Enter following URL in your browser

`http://localhost:8080/aws-java-app`

## Techniques used

- [Spring REST Service](https://spring.io/guides/gs/rest-service/)
- [Docker](http://www.docker.com)
- [CircleCI](http://circleci.com)
- [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/)
- [SeleniumHQ](http://seleniumhq.org)
