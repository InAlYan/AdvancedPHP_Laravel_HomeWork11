# Продвинутое программирование на PHP — Laravel
## Домашняя работа №11

---

Цели практической работы

Научиться:

— интегрировать регистрацию и аутентификацию пользователей;
— разрабатывать механизмы авторизации действий пользователей системы;
— проектировать ролевую модель системы.


Что нужно сделать:

В этой практической работе вы реализуете проект, в котором будут использованы механизмы авторизации и аутентификации пользователей.

### 1. Создайте новый проект Laravel или откройте уже существующий.

---
![new project](storage/app/private/img/1_0.png "new project")

---

### 2. Создайте новую ветку вашего репозитория от корневой (main или master).

### 3. Установите библиотеку Laravel Breeze composer require laravel/breeze.

### 4. Установите файлы библиотеки php artisan breeze:install.

### 5. Соберите фронтенд проекта с помощью команд npm install && npm run dev.

### 6. Перейдите на ваш сайт и проверьте работу механизмов регистрации и аутентификации.

### 7. Создайте контроллер UsersController командой php artisan make:controller UsersController.

### 8. Создайте в классе UsersController функцию index, которая вернёт список всех пользователей системы.

### 9. Напишите маршрут ‘/users’ в файле web.php.

### 10. Создайте миграцию, которая добавит поле is_admin типа boolean в таблицу users.

### 11. Создайте политику php artisan make:policy UserPolicy --model=User и напишите функцию.

public function viewAny(User $user)
{
return $user->is_admin;
}

### 12. Зарегистрируйте политику в классе AuthServiceProvider.

protected $policies = [
User::class => UserPolicy::class,
];

### 13. Используйте авторизацию действий пользователя внутри контроллера UsersController в функции index.
    $this->authorize('view-any', User::class);

### 14. Создайте двух пользователей, дайте одному из них роль администратора и попробуйте перейти на маршрут ‘/users’ вашего проекта сначала за неаутентифицированного пользователя, а далее за обычного пользователя и администратора системы.
