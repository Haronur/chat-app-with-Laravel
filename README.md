
## -- Laravel Default Authentication --

#### Step 1: Create Auth Scaffolding 
- You have to follow few steps to make auth in your laravel 8 application.
First, you need to install the laravel/UI package as like bellow:

```
composer require laravel/ui
php artisan ui vue --auth
npm install && npm run dev
```

#### Step 2: Create Database at phpMyAdmin named `laravel-chat` and setup .env file in your root directory 

- Database
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel-chat
DB_USERNAME=root
DB_PASSWORD=
```

#### Step 3: Customize at AppServiceProvider.php 
```
Customize at AppServiceProvider.php in project\app\Providers
```

#### Step 4: Migrate Database
- Now you need to run default migration of laravel by the following command:
```
php artisan migrate
```

#### Step 5: Run Server
```
php artisan serve
```
## -- Chatify Laravel Package Integration --

# Chatify Laravel Package
It is a Laravel package to add a complete real-time chat system to your application with one command line.

# Requirements
- PHP >=5.3.2.
- Laravel >=5.4
- Pusher Api Account.

# Features
 <img src="https://1.bp.blogspot.com/-KSPiLL3tq_o/XgpLmCgWAuI/AAAAAAAAA6w/n6m4k2MC1joNMgKS6Vpki2-3z92HXUvQwCLcBGAsYHQ/s1600/Screenshot%2Bfrom%2B2019-12-30%2B21-59-55.png" style="width:50%;" />

 - Users / groups(soon) chat system.
 - Real-time contacts list updates.
 - Favorites contacts list (Like stories style) and add to favorite button.
 - Saved Messages to save your messages online like Telegram messenger app.
 - Search functionality.
 - Contact item's last message indicator (e.g. You: ....).
 - Real-time user's active status.
 - Real-time typing indicator.
 - Real-time seen messages indicator.
 - Real-time internet connection status.
 - Upload attachments (Photo/File).
 - Shared photos, delete conversation.. (User's info right side).
 - Responsive design with all devices.
 - User settings and chat customization : user's profile photo, dark mode and chat color.
   with simple and wonderful UI design.

# Demo
- Video on YouTube - [Click Here](https://youtu.be/gjo74FUJJPI)

# Installation
Video Tutorial on YouTube - [Click Here](https://youtu.be/fNHI002mPGc)

OR

Follow the steps below :



#### 1. Install the package in your Laravel app

```sh
$ composer require munafio/chatify
```

#### 2. Pusher Api Settings
This package using Pusher Api, so you need to :
- Create account and modify `.env` file of your Laravel app with your api credentials.
- This package used a Pusher client events, and client events must be enabled for the application. You can do this in the `Settings` tab for your app within the Channels dashboard. <br/>
[Read more about Pusher 'Triggering client events'](https://pusher.com/docs/channels/using_channels/events#triggering-client-events)
<img src="https://1.bp.blogspot.com/-1N10R4h8tO0/XgoBH7Xw55I/AAAAAAAAA6Y/KBRG-W-PqSQfhq1rKAsv-B61VfiQvwgTgCLcBGAsYHQ/s1600/Screenshot%2Bfrom%2B2019-12-30%2B16-47-05.png" style="width:100%;"/>

#### 3. Publishing Assets
Packages' assets to be published :<br/>
The Important assets:
- config
- assets
- migrations

 and the optional assets :
- controllers
- views

to pusblish the assets, do the following command line with changing the tag value .. that means after `--tag=` write `chatify-` + asset name as mentioned above.<br/>
Example :
```sh
$ php artisan vendor:publish --tag=chatify-config
```
* NOTE: Publishing assets means (e.g. config) that creating a copy of the package's config file into the `config` folder of your Laravel applications and like so with the other asstes (Package's Views, controllers, migrations ...). 

#### 4. Migrations
Migrate the new `migrations` that added by the previous step 
```sh
$ php artisan migrate
```
#### 5. Storage Symlink
Create a shourtcut or a symlink to the `storage` folder into the `public` folder
```sh
$ php artisan storage:link
```

#### 6. App config
For Laravel `<=v5.4` that doesn't support package auto-discovery, add the following provider into `config/app.php` providers array list :
```php
...
/*
* Package Service Providers...
*/
\Chatify\ChatifyServiceProvider::class,
...
```

and the following alias into  into `config/app.php` aliases:
```php
...
/*
* Class Aliases
*/
'Chatify' => Chatify\Facades\ChatifyMessenger::class,
...
```

 * After installing the package, you can access the messeneger by the default path(route path) which is `/chatify`, and you can change path name in the config file `config/chatify.php` as mentioned in the `configurations` below.
##### That's it .. Enjoy :)

<br/>

# Configurations
You can find and modify the default configurations of the package at `config/chatify.php` file that you published in the step 2 of the installation steps .. and all configurations is documented well to be understood by other developers.
* All package’s files is documented to understand the whole code.

#### Messenger Name
This value is the name of the app which is used in the views or elsewhere in the app.
```sh
...
'name' => env('CHATIFY_NAME', 'Chatify Messenger'),
...
```

#### Messenger Path in Your App
This value is the path of the package or in other meaning, it is the prefix of all the registered routes in this package.
##### e.g (yourapp.domain/chatify)
```sh
...
'path' => env('CHATIFY_PATH', 'chatify'),
...
```


#### Package's web routes middleware
This value is the middleware of all routes registered in this package which is by default : `auth`.
```sh
...
'middleware' => env('CHATIFY_MIDDLEWARE', 'auth'),
...
```


#### Pusher API credentials
you don't need to modify the credentials of Pusher from here, because you already added your credentials in the `.env` file of your Laravel app.

#### User Avatar
This is the user's avatar setting that includes :
```sh
...
'user_avatar' => [
        'folder' => 'users-avatar',
        ...
    ],
...
```
which is the default folder name to upload and get user's avatar from.

```sh
...
'user_avatar' => [
        ...
        'default' => 'avatar.png',
    ],
...
```
which is the default avatar file name for users stored in database .. and when you publishing `assets`, a copy of the avatar photo will be copied into your storage path.

#### Attachments By Default
This array contains the important default values that used in this package :
```sh
...
'attachments' => [
        'folder' => 'attachments',
        ...
    ],
...
```
This is the default folder name for `attachments` in the storage which is all the attachments will be stored in .. and also going to be used in attachments urls in the views.

```sh
...
'attachments' => [
        ...
        'route' => 'attachments.download',
    ],
...
```
It is the route name of the `download attachments` method.

## Author 
[Munaf A. Mahdi](https://www.munafio.com/p/contact-me.html)

## License
[MIT](https://choosealicense.com/licenses/mit/)


### I have integrated this package in laravel 8 . But after following the above instruction I had to do extra two things is below:
- 1) copy CSS & js folder from ```vendor\munafio\chatify\assets ``` and paste to the public folder in the root of my app and 
- 2) As per laravel 8, I had to change
 `use App\Models\User;` to `use App\Models\User;`
 in the `MessagesController.php` file in the folder of```vendor\munafio\chatify\src\Http\Controllers``` 

###  Now it is working like laravel 6 version.
