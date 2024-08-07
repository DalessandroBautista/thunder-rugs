# Utilizar la imagen oficial de Node.js
FROM node:18

# Crear directorio de trabajo
WORKDIR /workspace

# Instalar dependencias necesarias para Atuin
RUN apt-get update && \
    apt-get install -y curl git sqlite3

# Descargar e instalar Atuin
RUN curl -sSL https://raw.githubusercontent.com/ellie/atuin/main/install.sh | bash

# Añadir Atuin al PATH
ENV PATH="/root/.local/bin:$PATH"

# Copiar package.json y package-lock.json
COPY my-next-app/package*.json my-next-app/
COPY my-nest-app/package*.json my-nest-app/

# Instalar dependencias para ambos proyectos
RUN cd my-next-app && npm install
RUN cd my-nest-app && npm install

# Copiar todo el código fuente
COPY my-next-app my-next-app
COPY my-nest-app my-nest-app

# Exponer puertos
EXPOSE 3000 3001

# Comando por defecto
CMD ["bash"]
