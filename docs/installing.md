
# Installing

There are a couple different methods of installation available to you depending on if you are installing GetRealT as a stand alone product or adding to another Laravel project.

## GetRealT Manager - Installer

A command line install tool that will install everything from scratch is available for download at;
<https://github.com/timitek/getrealt-manager>

GetRealT manager utilizes Composer to install it's components.  Make sure you have composer installed before continuing.

You can install the manager either locally and run it from the cloned repository, or globally in composers CLI tool set to make it available everywhere.

**Installing Globally**

```
composer global require "timitek/getrealt-manager"
```

Make sure to place the ```$HOME/.composer/vendor/bin``` directory (or the equivalent directory for your OS) in your $PATH so the ```getrealt``` executable can be located by your system.

**Installing Locally**

If you would prefer not to install getrealt-manager into your composer's home globally , you may install it locally and execute it from this local directory.

Choose the directory you would like to install int into and clone the repository;

```
git clone https://github.com/timitek/getrealt-manager.git
```

Make sure to either place this new directory into your $PATH, or create the appropriate alias in your .bashrc so that you can execute it.

Example..

```
alias getrealt="/home/[the path where it was installed]/getrealt-manager/getrealt"
```


***

### How To Use

The GetRealT manager allows you to create a fresh installation of GetRealT or perform maintenance on existing installations.

### Installing a new GetRealT site

To create a clean installation of a new GetRealT site or update an existing installation use the ```getrealt add``` command.

**Usage**
getrealt [options] < name >

*example*

```
getrealt add mysite
```

Then follow the prompts.

### Updating an existing GetRealT site

To update an existing site, use the --update option.

```
getrealt add mysite --update
```

If you don't want to change any of the settings during the update, but are only interested in applying updates, you can supply an answer file (typically this is the existing .env file), in order to suppress being prompted.

```
getrealt add mysite --update --answerfile=./<mysite>/.env
```


### Getting Help

To display help for getrealt at any time you can type;

```
getrealt help
```

To get help for a specific command;

```
getrealt help add
```


### List Of Commands

To display a list of available commands

```
getrealt help
```

### Manually adding to an existing project

Manual installation requires a configured Laravel installation with Quarx and GetRETS.

**Step 1:** Install Laravel (<https://laravel.com/docs/>).

**Step 2:** Install Quarx (<https://github.com/YABhq/Quarx#installation>).

**Step 3:** Install GetRealT for Quarx

```
composer require timitek/getrealt-quarx
```

*alternatively, for the latest bleeding edge development version use*

```
composer require timitek/getrealt-quarx:dev-master --dev
```

**Note**: *For Laravel 5.4 and older it is necessary to add the following to the providers section within config/app.php.*

```php
Timitek\GetRETS\Providers\GetRETSServiceProvider::class,
```

Make GetRealT the active Quarx theme by modifying the config/quarx.php and changing the value for the frontend-theme.

```php
'frontend-theme' => '../../vendor/timitek/getrealt-quarx/resources/views/theme'
```

Publish all of the assets with the following commands.

```
php artisan vendor:publish --provider="Timitek\GetRealT\Providers\GetRealTServiceProvider" --tag=config
```

```
php artisan vendor:publish --provider="Timitek\GetRealT\Providers\GetRealTServiceProvider" --tag=public
```

**Step 5:** Configure your site.

All of these settings can be configured directly from the quarx admin dashboard once your website is up and running from the GetRealT menu at /quarx/getrealt/settings.  However you may also manually modify the settings within the .env file.

**.env file note**: *If you modify the .env file directly, any values within the .env file that have spaces in them must be wrapped in double quotes ""*

**Map note**: *In order to display the maps on the listing details pages, obtain a google maps API key <https://developers.google.com/maps/documentation/javascript/get-api-key>*

Add values for the following settings to your .env file.

**GETRETS_CUSTOMER_KEY** = the customer key provided to you by timitek.com

**GETREALT_SITE_NAME** = What is the name you would like to use in the sites banner as the site name?

**GETREALT_THEME** = What is the initial theme you would like to use for the site?

**GETREALT_MAPS_KEY** = What is your google maps api key? <https://developers.google.com/maps/documentation/javascript/get-api-key>

**GETREALT_LEADS_EMAIL** = What e-mail address do you want your leads sent too?
                    

```
GETRETS_CUSTOMER_KEY=your_customer_key_from_timitek
GETREALT_SITE_NAME=GetRealT
GETREALT_THEME=united
GETREALT_MAPS_KEY=(Your Google maps API Key)
GETREALT_LEADS_EMAIL=support@timitek.com
```

***

## Further Information

For further documentation and information visit <http://www.getrealt.com> and <http://help.getrealt.com> or contact timitek at <http://www.timitek.com/getrealt>.
If you are interested in managed hosting / installation, visit <https://www.timitek.net>.

***


## Technonology Stack

**PHP Web Framework**: Laravel (<https://www.laravel.com/>)

**Content Management Library**: Quarx (<https://quarxcms.com/>)

**Listing Integration**: The Laravel module is provided by getrets-laravel (<https://github.com/timitek/getrets-laravel>)

**Cloud based RETS listing data API**: GetRETS (<http://www.timitek.com/>) - *A customer key is required for listing integration*