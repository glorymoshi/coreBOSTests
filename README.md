coreBOS Tests
=======

**core Business Operating System Tests**

Set of functional, unit and integrations tests and performance benchmarking scripts for the [coreBOS Project](http://corebos.org/).

The goal of the project is to create a set of automatic validations, more oriented towards [Behaviour-Driven Development](http://en.wikipedia.org/wiki/Behavior_driven_development) than unit tests, because unit tests would be overkill and extremely difficult for such a complex project. We will prefer and create functional and integration tests over unit tests although some unit tests will make it into the mix.

##Installation

Clone the the full [coreBOS repository](https://github.com/tsolucio/corebos). The coreBOS Tests project is a submodule inside the coreBOS github repository. So you will have to follow the typical steps to get the code from the submodule:

* git submodule init
* git submodule update

Next [install coreBOS normally](http://corebos.org/documentation/doku.php?id=en:install550). Then drop or empty the database that was created and fill it in with the test data you will find in build/coreBOSTests/database/coreBOSTests.sql.

You should be able to log in with the user and password "admin".

* go to coreBOS Updater, load and apply all changes (as always)
* go to Settings > Access Privileges and "Recalculate"

You should be able to run the different tests now.

##Test Execution

To launch the **functional/behaviour tests**, go into the root coreBOS directory and launch this command:

```build/coreBOSTests/phpunit -c build/coreBOSTests/phpunit.xml```

Optionally with debugging for more verbose output:

```build/coreBOSTests/phpunit --debug -c build/coreBOSTests/phpunit.xml```

If you want to execute the **integration tests**, you will need a selenium server. Then you can launch the tests with:

```build/coreBOSTests/phpunit -c build/coreBOSTests/integration.xml```

###Test browser

By default the integration tests are executed in firefox and chrome browsers, which are the two coreBOS officially supported browsers. You can add other browsers by adding the corresponding webdriver in your selenium server and changing the base integration test class which can be found at build/coreBOSTests/integration/cbIntegrationTest.php

###Individual tests suites
In the files build/coreBOSTests/phpunit.xml and build/coreBOSTests/integration.xml you will find definitions of the different test suites that can be launched indicidually if needed.

##Developing Tests

For functional and unit tests just follow phpunit good practices by creating test scripts in the same structure as the original file is with the recommended file naming conventions.

Then edit the test suites accordingly if necessary.

For integration tests the same rules apply except that the base class for tests is the one that coreBOSTests uses so all our integration tests inherit the two browser testing. You look at the existing examples but it basically means something like this:

```
<?php
require_once 'build/coreBOSTests/integration/cbIntegrationTest.php';

class YourIntegrationTest extends cbIntegrationTest
{
...
```

##License
MIT

**Thank you** very much for your help and contribution.

*coreBOS Team*
