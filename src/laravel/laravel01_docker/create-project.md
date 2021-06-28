# Laravelプロジェクト作成

```bash
$ curl -s https://laravel.build/laravel_todo | bash

 _                               _
| |                             | |
| |     __ _ _ __ __ ___   _____| |
| |    / _` | '__/ _` \ \ / / _ \ |
| |___| (_| | | | (_| |\ V /  __/ |
|______\__,_|_|  \__,_| \_/ \___|_|

Warning: TTY mode requires /dev/tty to be read/writable.
    Creating a "laravel/laravel" project at "./laravel_todo"
    Installing laravel/laravel (v8.5.20)
      - Downloading laravel/laravel (v8.5.20)
      - Installing laravel/laravel (v8.5.20): Extracting archive
...
```

```bash
...
Please provide your password so we can make some final adjustments to your application's permissions.

[sudo] password for taroosg:

Thank you! We hope you build something incredible. Dive in with: cd laravel_todo && ./vendor/bin/sail up

```


```bash
$ cd laravel_todo
$ ./vendor/bin/sail up -d
```

```bash
laravel_todo_laravel.test_1   start-container                  Exit 137
Shutting down old Sail processes...
Creating network "laravel_todo_sail" with driver "bridge"
Creating laravel_todo_mysql_1       ... done
Creating laravel_todo_mailhog_1     ... done
Creating laravel_todo_selenium_1    ... done
Creating laravel_todo_redis_1       ... done
Creating laravel_todo_meilisearch_1 ... done
Creating laravel_todo_laravel.test_1 ... done
```


ブラウザでlocalhostにアクセスし，下記画面が表示されればOK．


![トップ画面](../img/20210104-laravel-firstview.png)
