Oto przykład podstawowego Dockerfile dla aplikacji Node.js. Najpierw stwórzmy ten plik i wyjaśnię każdą jego część.

# Use official Node.js runtime as base image
FROM node:18-alpine

# Set working directory in container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci --only=production

# Copy application source code
COPY . .

# Expose port
EXPOSE 3000

# Start application
CMD ["node", "app.js"]

Wyjaśnię każdą linię tego Dockerfile:
FROM node:18-alpine - Używamy oficjalnego obrazu Node.js w wersji 18 opartego na Alpine Linux (lekka dystrybucja)
WORKDIR /usr/src/app - Ustawiamy katalog roboczy w kontenerze
COPY package*.json ./ - Kopiujemy pliki package.json i package-lock.json przed instalacją zależności (optymalizacja cache)
RUN npm ci --only=production - Instalujemy zależności produkcyjne używając npm ci (szybsze i bezpieczniejsze niż npm install)
COPY . . - Kopiujemy kod źródłowy aplikacji do kontenera
EXPOSE 3000 - Informujemy, że aplikacja będzie nasłuchiwać na porcie 3000
CMD ["node", "app.js"] - Definiujemy komendę startową aplikacji
Aby zbudować i uruchomić kontener, należy wykonać następujące komendy:
docker build -t my-node-app .
docker run -p 3000:3000 my-node-app

Dobre praktyki zastosowane w tym Dockerfile:
Używamy oficjalnego obrazu bazowego
Wykorzystujemy wieloetapowe kopiowanie dla lepszego wykorzystania cache
Używamy npm ci zamiast npm install
Instalujemy tylko zależności produkcyjne
Używamy Alpine Linux jako lekkiej bazy
Jasno definiujemy port aplikacji





# Use official Node.js runtime as base image
FROM node:18

# Set working directory in container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application source code
COPY . .

# Expose port
EXPOSE 3000

# Start application using npm start
CMD ["npm", "start"]

Stworzyłem Dockerfile dokładnie według Twoich wymagań. Oto wyjaśnienie każdej linii:
FROM node:18 - używamy oficjalnego obrazu Node.js w wersji 18
WORKDIR /usr/src/app - ustawiamy katalog roboczy w kontenerze
COPY package*.json ./ - kopiujemy pliki package.json i package-lock.json
RUN npm install - instalujemy wszystkie zależności
COPY . . - kopiujemy pozostałe pliki aplikacji
EXPOSE 3000 - informujemy, że aplikacja będzie używać portu 3000
CMD ["npm", "start"] - ustawiamy komendę startową na "npm start"

Aby zbudować i uruchomić kontener, możesz użyć następujących komend:
docker build -t my-node-app .
docker run -p 3000:3000 my-node-app

Pamiętaj, że aby to działało, Twój package.json musi zawierać skrypt start w sekcji scripts.