# 📦 Pterodactyl Register
Pterodactyl Register Module, this is usefull if you want to have a registration page in your pterodactyl panel for your clients to register

## ⚙️ Configuration

### 📄 File Placement
Copy/Paste __RegisterController.php__ to __YOUR PTERODACTYL FOLDER /app/Http/Controllers/__<br>
Copy/Paste __RegisterContainer.tsx__ to __YOUR PTERODACTYL FOLDER /resources/scripts/components/auth__

### 🔑 Api key
You need to make a apikey in the admin panel with the read/write perms on "Users"
and then copy the key and replace it in the `RegisterController.php` where it says *YOURAPIKEYHERE* on line __75__
also don't forget to replace *YOURWEBSITEURL* to your website url on line __65__

### 🔗 Routes
Add these lines at `YOUR PTERODACTYL FOLDER routes/auth.php`:<br>

<br>

> **if you are on version __1.7.0__:**<br>
```php
Route::get('/register', [RegisterController::class, 'index'])->name('auth.register');
```
and the below route should be under `Route::middleware(['throttle:authentication'])`
```php
Route::post('/register', [RegisterController::class, 'register'])->name('auth.register.url')->middleware('recaptcha');
```

<br>

> **if you are on version __1.8.x__:**<br>
```php
Route::get('/register', [Auth\RegisterController::class, 'index'])->name('auth.register');
```
and the below route should be under `Route::middleware(['throttle:authentication'])`
```php
Route::post('/register', [Auth\RegisterController::class, 'register'])->name('auth.register.url')->middleware('recaptcha');
```

<br>

Add this line at `YOUR PTERODACTYL FOLDER /resources/scripts/routers/AuthenticationRouter.tsx`:<br>
```php
<Route path={`${path}/register`} component={RegisterContainer} exact/>
```

# 🎟️ Support
This Module supports pterodactyl __1.7.x__
for older versions i have not tested but you can do that and also
if you encounter problems or your confused open an issue and i'll try to solve it :D

# 📄 Lisence
This Pterodactyl Module is Lisenced under: **GNU General Public Lisence 3.0**
