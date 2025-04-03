FROM node:22.14.0

# Atualiza pacotes do sistema
RUN apt-get update && apt-get install -qq -y --no-install-recommends

# Define diretório de trabalho
ENV INSTALL_PATH /barber-shop-ui
RUN mkdir -p $INSTALL_PATH
WORKDIR $INSTALL_PATH

# Copia arquivos de dependências primeiro
COPY package*.json ./

# Limpa o cache do npm e instala dependências sem opcionais
RUN npm cache clean --force
RUN npm install --no-optional --legacy-peer-deps --force

# Instala o Angular CLI globalmente
RUN npm install -g @angular/cli@19.1.5

# Copia o restante dos arquivos
COPY . .

# Expor porta Angular
EXPOSE 4200

# Iniciar a aplicação
CMD ["npm", "start"]
