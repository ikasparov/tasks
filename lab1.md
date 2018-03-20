# Лабораторная 1

Методичка по лабораторным

### Настройка окружения

```bash
// Настройка RVM
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
$ \curl -sSL https://get.rvm.io | bash -s stable

$ rvm install ruby // Установка руби

$ gem install bundler // установка сборщика пакетов
$ gem install rails // установка Ruby on Rails

$ rails new <название> // создание приложения
```

### Запуск сервера

Для запуска сервера необходимо зайти в папку с проектом с помощью команды `cd` и выполнить следующую команду:

```
$ rails server
```

По умолчанию сайт будет доступен по адресу `localhost:3000`

### Создание модели

Далее необходимо настроить модели и связи в базе данных. Для автоматического создания модели и миграции воспользуемся генераторами rails:

```
$ rails generate model Word
```

Данная команда сгенерирует 2 файла со следующим содержимым:

`app/models/word.rb:`
```ruby
class Word < ApplicationRecord
end
```

`db/migrate/20180315070951_create_words.rb`
```ruby
class CreateWords < ActiveRecord::Migration[5.1]
  def change
    create_table :words do |t|

      t.timestamps
    end
  end
end
```

Далее настроим поля для модели:

```ruby
class CreateWords < ActiveRecord::Migration[5.1]
  def change
    create_table :words do |t|

      t.string :ru, nil: false
      t.string :en, nil: false

      t.timestamps
    end
  end
end

```

После добавления и настройки полей для базы данных в миграции необходимо выполнить миграцию командой:
```bash
$ rails db:migrate
```