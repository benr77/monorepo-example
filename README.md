Monorepo Example
=====

Example repository to demonstrate configuration of a monorepo, using the `symplify/monorepo-builder` package.

### Repositories

* Monorepo - https://github.com/benr77/monorepo-example
* App1 - https://github.com/benr77/monorepo-app1
* App2 - https://github.com/benr77/monorepo-app2

### Configuration Steps

* Two vanilla Symfony apps installed in `apps/app1` and `apps/app2` using standard composer installation.
  * `cd apps && composer create-project symfony/website-skeleton:^4.4 app1`
  * `cd apps && composer create-project symfony/skeleton:^4.4 app2`
  
* Install some varying bundles in the two apps
  * `cd apps/app1 && composer require symfony/webpack-encore-bundle` 
  * `cd apps/app2 && composer require api` 

* Remove app vendor directories `rm -rf apps/app1/vendor apps/app2/vendor`

* Namespaces updated for each app to `MyCompany\App1` and `MyCompany\App2` etc

* Run `composer require --dev symplify/monorepo-builder`

* Create `monorepo-builder.yml` configuration file

* Run `vendor/bin/monorepo-builder merge` to combine the two app composer.json files in to a single composer.json in the monorepo root.

* Update monorepo vendor packages `composer update`

* Configure monorepo itself
  * `git init`
  * `git add *`
  * `git commit -a -m "Initial commit"`
  * `git remote add origin git@github.com:benr77/monorepo-example.git`
  * `git tag v0.0.1`
  * `git push -u origin master`

* Run `vendor/bin/monorepo-builder split` to split and push the individual apps to their respective repositories.



