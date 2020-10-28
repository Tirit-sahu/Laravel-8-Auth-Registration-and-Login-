Step 1: Install a new Laravel app
composer create-project laravel/laravel projectapp --prefer-dist

The command above only install Laravel, however, if you want to install Jetstream together then either

Laravel new projectapp --jet

or

composer require laravel/jetstream

we are going with the first of only installing Laravel, I want to explain other things in the process.

I highlighted some changes noticed in the installation of Laravel 8 from the previous Laravel versions, you can check them out in my previous post Laravel 8 CRUD.

Step 2: Database Setup
Open the .env file on your IDE or text editor

.env file
Change the DB_DATABASE to the name of your database and if you have set a Username and password for your phpmyadmin, specify it, otherwise, leave the username as root and password blank.
Before we migrate, let’s catch one bug before it throws an error, go to App/Providers/AppServiceProvider.php
and add

Schema::defaultstringLength(191);

to the boot function, also add

use Illuminate\Support\Facades\Schema;

to the top
AppServiceProvider file

Step 3: Migration
php artisan migrate

migration file

Step 4: install Jetstream
composer require laravel/jetstream

Installing Jetstream
Laravel advises that Jetstream and its stacks (livewire or inertia) should be done on a fresh application because it will install a layout view, registration, and login views, as well as routes for all authentication end-points. A dashboard route will also be generated for post-login requests. So an application that has some of those, might throw some conflicts.

Step 5: Install livewire or inertia
We need to install one of the stacks, either a livewire or an inertia stack, in this tutorial, I will only be using livewire because it set up everything I need for the app

php artisan jetstream:install livewire

Installing Livewire
As suggested, run npm install && npm run dev to build all the javaScript files and CSS we need for our app. On successful build, Laravel will send a notification at the bottom left.
Laravel Notification

Step 5: Migrate the new table that is created
php artisan migrate

migration Command
Let’s run our app

php artisan serve

Running our app
Holding down the Ctrl button and Clicking the localhost http://127.0.0.1:8000/ will serve our app in our default browser
