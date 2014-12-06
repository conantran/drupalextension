# Behat Drupal Extension

The Drupal Extension is an integration layer between [Behat](http://behat.org), [Mink Extension](https://github.com/Behat/MinkExtension), and Drupal. It provides step definitions for common testing scenarios specific to Drupal sites.

[![Build Status](https://travis-ci.org/jhedstrom/drupalextension.png?branch=3.0)](https://travis-ci.org/jhedstrom/drupalextension)

The Drupal Extension 3.0 supports Drupal 7 and 8, and utilizes Behat 3. For Drupal 6 support (or Behat 2), use the [1.0 version](https://github.com/jhedstrom/drupalextension/tree/1.0).

[![Latest Stable Version](https://poser.pugx.org/drupal/drupal-extension/v/stable.svg)](https://packagist.org/packages/drupal/drupal-extension) [![Total Downloads](https://poser.pugx.org/drupal/drupal-extension/downloads.svg)](https://packagist.org/packages/drupal/drupal-extension) [![Latest Unstable Version](https://poser.pugx.org/drupal/drupal-extension/v/unstable.svg)](https://packagist.org/packages/drupal/drupal-extension) [![License](https://poser.pugx.org/drupal/drupal-extension/license.svg)](https://packagist.org/packages/drupal/drupal-extension) [![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/jhedstrom/drupalextension/badges/quality-score.png?b=3.0)](https://scrutinizer-ci.com/g/jhedstrom/drupalextension/?branch=3.0)



## Use it for testing your Drupal site.

[Full documentation](https://behat-drupal-extension.readthedocs.org)

1. You'll need something resembling this `composer.json` file

  ``` json
    {
      "require": {
        "drupal/drupal-extension": "~3.0"
      },
      "config": {
        "bin-dir": "bin/"
      }
    }
  ```

1. Then run

  ``` bash
  php composer.phar install
  ```

  To download the required dependencies. If composer isn't installed

  ``` bash
  curl -s https://getcomposer.org/installer | php
  ```

1. At a minimum, your `behat.yml` file will look like this

  ``` yaml
  default:
    suites:
      default:
        contexts:
          - Drupal\DrupalExtension\Context\DrupalContext
    extensions:
      Behat\MinkExtension:
        goutte: ~
        selenium2: ~
        base_url: http://git6site.devdrupal.org/
      Drupal\DrupalExtension:
        blackbox: ~
  ```

1. Start adding your feature files to the `features` directory of your repository.

1. The Drupal Extension is capable of discovering additional step-definitions provided by subcontexts. Module authors can provide these in files following the naming convention of `foo.behat.inc`. Once that module is enabled, the Drupal Extension will load these.

  Additional subcontexts can be loaded by either placing them in the bootstrap directory (typically `features/bootstrap`) or by adding them to `behat.yml`.

  ``` yaml
    Drupal\DrupalExtension:
      subcontexts:
	    paths:
	      - "/path/to/additional/subcontexts"
		    - "/another/path"
  ```

  To disable automatic loading of subcontexts:

  ``` yaml
    Drupal\DrupalExtension:
      subcontexts:
	    autoload: 0
  ```

## Additional resources

 * [Behat Drupal Extension documentation](https://behat-drupal-extension.readthedocs.org)
 * [Behat documentation](http://docs.behat.org)
 * [Mink documentation](http://mink.behat.org)

## Examples and code snippets

 * [Complex node creation, with field collections and entity references](https://gist.github.com/jhedstrom/5708233)
 * [Achievements module support](https://gist.github.com/jhedstrom/9633067)
 * [Drupal form element visibility](https://gist.github.com/pbuyle/7698675)
 * [Track down PHP notices](https://www.godel.com.au/blog/use-behat-track-down-php-notices-they-take-over-your-drupal-site-forever)
 * [Support for sites using basic HTTP authentication](https://gist.github.com/jhedstrom/5bc5192d6dacbf8cc459)
