## Listing App
- A modern listing application built using Laravel, Inertia.js, and Vue.js. This app supports CRUD operations for listings and features a responsive UI, server-side validation, and user authentication.
  
## Tech Stack
- Backend: Laravel 
- Frontend: Vue 3 + Inertia.js
- Styling: Tailwind CSS 
-  Database: SQlite

##  Features
- User Authentication (Login/Register)
- Create, Read, Update, Delete Listings
- Server-side form validation
- Pagination 
- Flash messages and error handling via Inertia
- Responsive design
- Middleware-protected routes


## After cloning this repo, do the following steps:
1. `composer install`
2. `npm install`
3. Duplicate the `.env.example` file and rename it to `.env`
4. Create the `database.sqlite` in database directory
5. Run `php artisan migrate`
6. Run `php artisan key:generate`
7. Run `php artisan serve`
8. Run `npm run dev`




## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

