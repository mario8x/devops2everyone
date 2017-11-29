# Testing Knowledge
https://www.joecolantonio.com/2017/10/31/13-scary-test-automation-practices/



# Need to have

## Automation framework:

* Need to have more time to understand the current automation framework. We support a lot of advanced features in the current automation testing framework.

* The current framework need to go through a lot of steps to develop a test suite (define test suite, define test cases, define test steps, link with test step functions, call object actions, find element and save element in excel file).
I suggest that we should review, refactor, and improve the current test framework. We shouldn't develop a new framework.

* Need to have the statistic analysis of code quality to check duplicated code.

## Automation Strategies:
0. Team collaboration

* Need to have some one to research and apply some testing techniques as (stress test, security test). Both US team and VN team have no knowledge of these types of testing.

1. Automation test

* Need to deeply have domain knowledge of all modules then we can apply test techniques(flow test, scenarios test, risk test). This is a
first step to help us involve in their regression test

* Auto installation: need to request to develop test for modules: Analytic, Custom, Inventory, Transportation Planning and Management, Retail Optimization

* Smoke test: If the smoke test is too big for multiple modules we need to separate them into single module.

2. Deployment: need to integrate our current tests into their deployment pipelines (CI).

3. Environment:
  * Infrastructure testing: currently we've been doing that (check db updated, check cobols modules, check logs, run build verification test)
  * Destructive testing: Ask clients about this testing which include: failover , recovery after failure of service, back up and restore of a file system, stop database processes, restart environment unexpectedly. I'm not sure that is applicable for this project or not.
  * Need to have right on testing environment.(local, tara's environment, and testing environment)
  * Log monitoring: need to understand some additional logs which we have no knowledge of them. We can find some bugs which happen unexpectedly.  
