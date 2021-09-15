# Хранилище файлов с доступом по http

Реализовать демон, который предоставит HTTP API для загрузки (upload) ,
скачивания (download) и удаления файлов.

#### Upload:
- получив файл от клиента, демон возвращает в отдельном поле http
response хэш загруженного файла
- демон сохраняет файл на диск в следующую структуру каталогов:
   store/ab/abcdef12345...
где "abcdef12345..." - имя файла, совпадающее с его хэшем.
/ab/ - подкаталог, состоящий из первых двух символов хэша файла.
Алгоритм хэширования - на ваш выбор.

#### Download:
Запрос на скачивание: клиент передаёт параметр - хэш файла. Демон ищет
файл в локальном хранилище и отдаёт его, если находит.

#### Delete:
Запрос на удаление: клиент передаёт параметр - хэш файла. Демон ищет
файл в локальном хранилище и удаляет его, если находит.

## Установка зависимостей
pip3 install -r requirements.txt

### Запуск Демона
python app.py abs_path_to_store --host=127.0.0.1 --port=5000

#### Параметры командной строки
path_store - абсолютный путь c названием хранилища(обязательный параметр) <br>
host - хост сервера (по умолчанию 127.0.0.1 ) <br>
port - порт сервера (по умолчанию  5000 ) <br>