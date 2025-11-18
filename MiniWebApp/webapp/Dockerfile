FROM python:3.11-slim

# Evitar buffering de logs
ENV PYTHONUNBUFFERED=1

# Directorio de trabajo
WORKDIR /app

# Dependencias del sistema para poder compilar mysqlclient (MySQLdb)
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        build-essential \
        default-libmysqlclient-dev \
        pkg-config && \
    rm -rf /var/lib/apt/lists/*

# Copiar código de la app
COPY . /app

# Instalar dependencias de Python
# Si existe requirements.txt lo usamos; si no, instalamos a mano lo típico de la MiniWebApp
RUN if [ -f requirements.txt ]; then \
      pip install --no-cache-dir -r requirements.txt; \
    else \
      pip install --no-cache-dir \
        Flask \
        Flask-SQLAlchemy \
        Flask-Login \
        mysqlclient; \
    fi

# Variables de entorno para Flask
ENV FLASK_APP=run.py
ENV FLASK_RUN_HOST=0.0.0.0
ENV FLASK_RUN_PORT=5000

EXPOSE 5000

CMD ["flask", "run"]
