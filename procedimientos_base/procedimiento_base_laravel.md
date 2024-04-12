# CORRER MIGRACIONES
- Comando
php artisan migrate

# RECURSOS PARA INSTTALACIÓN:
https://www.binaryboxtuts.com/php-tutorials/laravel-8-json-web-tokenjwt-authentication/

# INSTALAR JWT
- comando
composer require tymon/jwt-auth

- publicar el servicio en el service provider:
php artisan vendor:publish --provider="Tymon\JWTAuth\Providers\LaravelServiceProvider"

- generando el key secret 
php artisan jwt:secret

- en auth.php:
        'api' => [
            'driver' => 'jwt',
            'provider' => 'users',
            'hash' => false,
        ],

- en user.php (MODEL), implementar e importar esta interface:
use Tymon\JWTAuth\Contracts\JWTSubject;
 
class User extends Authenticatable implements JWTSubject

- copiar estos métodos:
     /**
     * Get the identifier that will be stored in the subject claim of the JWT.
     *
     * @return mixed
     */
    public function getJWTIdentifier()
    {
        return $this->getKey();
    }
 
    /**
     * Return a key value array, containing any custom claims to be added to the JWT.
     *
     * @return array
     */
    public function getJWTCustomClaims()
    {
        return [];
    }

-  Crear este controlador:
php artisan make:controller AuthController

# INSTALARA API.PHP
- Comando
php artisan install:api

# INSTALAR LARAVEL 10
- Comando:
composer create-project --prefer-dist laravel/laravel api-ecommerce-v10 "10.*"

# MODIFICANDO EL config/auth.php
- Código:

'guards' => [
        'web' => [
            'driver' => 'session',
            'provider' => 'users',
        ],
 
        'api' => [
            'driver' => 'jwt',
            'provider' => 'users',
            'hash' => false,
        ],
    ],

# LIMPIAR CACHE
- Comando:
php artisan cache:clear

# MIGRACIONES:
- Crear migración para agregar columna:
php artisan make:migration add_type_user_column_to_users_table --table=users

php artisan make:migration add_surname_column_to_users_table --table=users

- agregar propiedaddes a la amigración:
->nullable()
->default('A')

- correr migraciones:
php artisan migrate
