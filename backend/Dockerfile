# Используем официальный образ Python 3.12
FROM python:3.12

# Устанавливаем необходимые системные пакеты
RUN apt-get update && \
    apt-get install -y python3-setuptools && \
    rm -rf /var/lib/apt/lists/*


# Устанавливаем рабочую директорию
WORKDIR /app

RUN pip install gunicorn==23.0.0

# Копируем и устанавливаем зависимости Python
COPY requirements.txt .
RUN pip install --upgrade pip && \
    pip install -r requirements.txt --no-cache-dir

# Копируем остальные файлы проекта
COPY . .

# Запускаем сервер разработки Django
#CMD ["python", "manage.py", "runserver", "0:8000"]
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]
