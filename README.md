# Laravel + Vue.js MVP
***

The beta version for School management system.

Key Technologies:

- Laravel v9.0

- Vue.js v2.3.3

- Vue-Resource v1.3.4

- Vuex v2.3.1

- Vue-Router v2.5.3

- Moment.js v2.18.1

- Bootstrap-Sass v3.3.7

- Dockerize the DEV/Staging environments (compatible with Linux/Debian, MacOS, Windows 7)


## Prerequisites for LAMP(Linux/Apache/MySQL/PHP) stack

1) Install PHP 7.0 or 7.1 (reference: [installation in ubuntu](https://tecadmin.net/install-php-7-on-ubuntu/))

2) Install MySQL v5.7 (reference: [installation in ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-14-04))

3) Install Apache2 (reference: [installation in ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04))

4) Install Composer (reference: [installation in ubuntu](https://askubuntu.com/questions/736537/installing-composer))

5) Install Node.js v6.x & Npm v3.10.0 (reference: [installation in ubuntu](https://askubuntu.com/questions/594656/how-to-install-the-latest-versions-of-nodejs-and-npm-for-ubuntu-14-04-lts))

6) Upgrade Npm to v5.3.0 (`$ sudo npm install npm -g`)

7) Install php extensions 

- In the case of PHP v7.0 (`$ sudo apt-get install php7.0-fpm php7.0-dom php7.0-intl php7.0-mbstring php7.0-xml php7.0-mysql php7.0-curl php7.0-mcrypt php7.0-cli php7.0-dev php7.0-zip php7.0-gd`)

- In the case of PHP v7.1 (`$ sudo apt-get install php7.1-fpm php7.1-dom php7.1-intl php7.1-mbstring php7.1-xml php7.1-mysql php7.1-curl php7.1-mcrypt php7.1-cli php7.1-dev php7.1-zip php7.1-gd`)

## Application Setup in the Dev Environment

In the case of Docker usage...

Clone repository git@bitbucket.org:xxx/dev-infrastructure.git. 
Then go to ./volumes/datavol folder and clone git@bitbucket.org:xxx/laravel-vue-mvp.git repository to laravel-vue-mvp folder, checkout your dev branch (or staging branch)

In the case of LAMP usage...

Clone git@bitbucket.org:xxx/laravel-vue-mvp.git repository to laravel-vue-mvp folder, checkout your dev branch (or staging branch)

In the /laravel-vue-mvp folder,

1) Create a .env file copying from .env.dev or .env.example.

2) Run `$ composer install` to install the necessary dependencies.

3) Run `$ npm install --force` to install the node modules & libraries by NPM. 

4) Run `$ npm run dev` to compile the JS/SCSS into a single files by Laravel Mix + Webpack.

5) Run `$ php artisan config:cache` to reflect the .env configuration.

6) Run `$ php artisan migrate --seed` to migrate and seed the data in DB.

7) Run `$ php artisan migrate:importdata` to import some data from the external resources. 

8) To start the scheduler itself, we only need to add one cron job on the server (using the `crontab -e` command), which executes `php /path/to/artisan schedule:run` every minute in the day. 
To discard the cron output we put `/dev/null 2>&1` at the end of the cronjob expression. `* * * * * php /path/to/artisan schedule:run 1>> /dev/null 2>&1`

## Running the application with LAMP stack on localhost

Clone git@bitbucket.org:xxx/laravel-vue-mvp.git repository to laravel-vue-mvp folder, checkout your dev branch (or staging branch)

In the /laravel-vue-mvp folder,

- Create a directory to store the downloadable files(.pdf & .xls) temporarily. (`$ mkdir -p public/files`)

- File permissions (`$ sudo chmod -R 777 storage bootstrap/cache public/files`)

- Create Apache VirtualHost. (reference: [configuration in ubuntu](https://tecadmin.net/install-laravel-framework-on-ubuntu/))

## Running the application with docker on localhost

In the root folder of dev-infrastructure, 

- Fresh-build and rebuild the docker containers: `$ docker-compose -f docker-compose.dev.yml up --build`.

- Run the prebuilt containers: `$ docker-compose -f docker-compose.dev.yml up`. 

- Run the containers in background: `$ docker-compose -f docker-compose.dev.yml up -d`. 

- Stop the running all containers: `$ docker-compose kill`.


## Command Line Tools

- nodejs: v6.10.3

- NPM: v5.0.0

- vue-cli: v2.8.1

- git: v2.13.0

## Coding Style

- Use [PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md) and [PSR-4](http://www.php-fig.org/psr/psr-4/) coding standards.

- PHP tab size is 4.

- Blade/HTML tab size is 2.

- SCSS/JavaScript tab size is 4.

- Translate tabs to spaces.

- Ensure newline at end of file.

- Trim trailing white space.

## Tips for VueJS

- Vue.js can be written in the recommended ECMAScript 6.

- This command `$ npm run watch` can help you with compiling the Vue/JS/SCSS/Images changes immediately. 
After you write/change some code, please hit `CTRL + S` in your IDE. Then you can see the compiling process via terminal.

- See the [Laravel <-> Vue & Vuex in our SPA]
