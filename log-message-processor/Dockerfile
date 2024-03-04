# Usa la imagen base de Python 3.6
FROM python:3.6

# Establece el directorio de trabajo en /app
WORKDIR /app

# Copia el archivo de requisitos a la imagen
COPY requirements.txt .

# Instala las dependencias del servicio
RUN pip install --no-cache-dir -r requirements.txt

# Copia el código fuente al contenedor
COPY . .

# Comando para ejecutar el servicio
CMD ["python3", "main.py"]