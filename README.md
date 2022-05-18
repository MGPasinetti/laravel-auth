Esercizio di oggi: Laravel Boolpress
nome repo: laravel-auth
Ciao ragazzi,
creiamo con Laravel la nostra alternativa al più famoso CMS del modo: WordPress.
Oggi iniziamo un nuovo progetto che si arricchirà nel corso delle prossime lezioni: man mano aggiungeremo funzionalità e vedremo la nostra applicazione crescere ed evolvere.
Nel pomeriggio, rifate ciò che abbiamo visto insieme stamattina stilando tutto a vostro piacere utilizzando Sass.

# Progetto Laravel con login
## Inizializzazione

1. Creare la cartella del progetto
1. Entrare dal terminale nella cartella
1. composer create-project --prefer-dist laravel/laravel:^7.0 .
1. Only for Laravel <= 7
    - composer remove fzaninotto/faker
    - composer require fakerphp/faker
1. Se volete usare la laravel-debugbar
    - composer require barryvdh/laravel-debugbar --dev
1. composer require laravel/ui:^2.4
1. php artisan ui vue --auth
1. (eventuali altre librerie per altre cose come: gestione ruoli, generazione slug)
1. Su package.json modificare:
    - "bootstrap": "^4.0.0", in "bootstrap": "^5.1.3", (o comunque la versione che si vuole usare)
    - "popper.js": "^1.12", in "@popperjs/core": "^2.11.5",
1. Su resorces/js/bootstrap.js commentare:
    - window.Popper = require('popper.js').default;
    - window.$ = window.jQuery = require('jquery');
1. npm install
1. php artisan make:model --all Post
1. Spostare il file app/Http/Controllers/HomeController.php nella cartella Admin
1. Nel file appena spostato:
    - modificare namespace App\Http\Controllers; in namespace App\Http\Controllers\Admin;
    - aggiungere una riga nuova con use App\Http\Controllers\Controller;
1. Cancellare il controller generato in app/Http/Controllers
1. php artisan make:controller --model=Post Admin/PostController
1. composer dump-autoload
1. Nel file app/Providers/RouteServiceProvider.php modificare:
    - public const HOME = '/home'; in public const HOME = '/admin'; (oppure quello che avete messo- voi)
1. Se serve modificare il file app/Http/Middleware/Authenticate.php:
    - return route('login'); con la route che volete voi

## Database

1. Creare il database da phpMyAdmin oppure da linea di comando o come volete
1. Nel file .env aggiornare i dati del database (quelli che iniziano con DB_) e giacchè anche1. APP_NAME col nome della vostra app
1. Aggiornare i file delle migrations
1. Aggiornare il file DatabaseSeeder.php aggiungendo $this->call(ModelSeeder::class); per ogni1. model di cui abbiamo il seeder
1. Aggiornare i file dei seeders
    - agiungere use Faker\Generator as Faker;
    - modificare public function run() a public function run(Faker $faker)
1. (slugs)
1. Nel model impostare la proprietà $fillable con le colonne che possono essere "mass assigned"

## Views

1. Organizzare la cartella resources/views con:
    - una sottocartella admin (con le sottocartelle per ciascun model risorsa) e spostare home- blade.php dentro admin
    - una sottocartella guests

## Avviare l'ambiente locale

1. npm run watch
1. php artisan serve

CHIUDERE TUTTE LE TAB IN VISUAL STUDIO CODE

