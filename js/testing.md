# Testing JavaScript


Unit tests, integration tests, and functional tests are all types of automated tests which form essential cornerstones of continuous delivery, a development methodology that allows you to safely ship changes to production in days or hours rather than months or years


## Cost of neglecting test
- They interrupt the user experience, which can cost you in sales, usage metrics, they can even drive customers away permanently.

- Bug fixes are interruptions which cause a costly context switch. Each interruption can waste up to 20 minutes per bug, not counting the actual fix.

- Bug diagnosis happens outside the normal context of feature development, sometimes by different developers who are unfamiliar with the code and the surrounding implications of it.

- Opportunity cost: The development team must wait for bug fixes before they can continue working on the planned development roadmap.

## Different Type of test

Each type of test has a unique role to play. You don’t choose between unit tests, functional tests, and integration tests. Use all of them, and make sure you can run each type of test suite in isolation from the others.

1. Unit Tests
ensure that individual components of the app work as expected. Assertions test the component API.

2. Integration Tests
ensure that component collaborations work as expected. Assertions may test component API, UI, or side-effects (such as database I/O, logging, etc…)

3. Functional Tests

 ensure that the app works as expected from the user’s perspective. Assertions primarily test the user interface.


You should isolate unit tests, integration tests, and functional tests from each other so that you can easily run them separately during different phases of development. During continuous integration, tests are frequently used in three ways:



* During development

for developer feedback. Unit tests are particularly helpful here.

* In the staging environment

to detect problems and stop the deploy process if something goes wrong. Typically the full suite of all test types are run at this stage.

* In the production environment

a subset of production-safe functional tests known as smoke tests are run to ensure that none of the critical functionality was broken during the deploy process.


Which Test Types Should You Use? All of Them.



## Unit Test

Realtime Developer Feedback


Unit tests ensure that individual components work in isolation from each other. Units are typically modules, functions, etc…

Unit tests should be:

- Dead simple.
- Lightning fast.
- A good bug report.


## Integration Tests

At some point, your code communicates with a database, file system or another third party. It could even be another module in your app.

That piece of implementation should be tested by integration tests. They typically have a more complicated setup that involves preparing testing environments, initializing dependencies, and so on.

## Functional Tests

Functional tests are automated tests which ensure that your application does what it’s supposed to do from the point of view of the user. Functional tests feed input to the user interface, and make assertions about the output that ensure that the software responds the way it should.


Functional tests are sometimes called end-to-end tests because they test the entire application, and it’s hardware and networking infrastructure, from the front end UI to the back end database systems. In that sense, functional tests are also a form of integration testing, ensuring that machines and component collaborations are working as expected.


## Smoke Test

After you deploy a new release to production, it’s important to find out right away whether or not it’s working as expected in the production environment.


## Running Tests

- Test can run in browser by creating an HTML page with the test libraries and test files included as JS Scripts.

- Tets Can run in headless browser

- Test can also be execuded in Node.js

## Test Tools Types

1. Test Launcher
are used to launch tests in the browser or Node.js with user config. (Karma, Jasmine, Jest, TestCafe, Cypress, webdriverio)

2. Testing structure providers help you arrange your tests in a readable and scalable way. (Mocha, Jasmine, Jest, Cucumber, TestCafe, Cypress)

3. Assertion functions are used to check if a test returns what you expect it to return and if its’t it throws a clear exception. (Chai, Jasmine, Jest, Unexpected, TestCafe, Cypress)

4. Generate and display test progress and summary. (Mocha, Jasmine, Jest, Karma, TestCafe, Cypress)

5. Mocks, spies, and stubs to simulate tests scenarios, isolate the tested part of the software from other parts, and attach to processes to see they work as expected. (Sinon, Jasmine, enzyme, Jest, testdouble)

6. Generate and compare snapshots to make sure changes to data structures from previous test runs are intended by the user’s code changes. (Jest, Ava)

7. Generate code coverage reports of how much of your code is covered by tests. (Istanbul, Jest, Blanket)

8. Browser Controllers simulate user actions for Functional Tests. (Nightwatch, Nightmare, Phantom, Puppeteer, TestCafe, Cypress)

9. Visual Regression Tools are used to compare your site to its previous versions visually by using image comparison techniques.


## Jest

## Mocha

## Karma

## Puppeteer



## Continuous Delivery

Prior to the continuous delivery revolution, software was released using a waterfall process.

### Waterfall Process

1. Requirement gathering
2. Design
3. Implementation
4. Verification
5. Deployment
6. Maintenance

It’s called waterfall because if you chart it with time running from right to left, it looks like a waterfall cascading from one task to the next. In other words, in theory, you can’t really do these things concurrently.


### Continuous Delivery

Continuous delivery is a development methodology that acknowledges that scope is uncovered as the project progresses, and encourages incremental improvements to software in short cycles that ensure that software can be released at any time without causing problems.



