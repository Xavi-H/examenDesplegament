# examenDesplegament

## Arquitectura de l'aplicació

L'aplicació es compon de dos serveis gestionats amb Docker Compose:

Servei:
- web: php:8.2-apache, port: 8080 → 80 es un servidor apache i php que fa servir la aplicació
- db: mysql:8.0, port: 3306 la base de dades Mysql

### Xarxa

Docker Compose crea automàticament una xarxa interna que connecta els dos serveis. El servei web es comunica amb db usant el nom de servei com a hostname (DB_HOST: db).

---

## Requisits previs

- Git instal·lat
- Docker i Docker Compose instal·lats
- Compte a GitHub (per clonar el repositori)
- Per al desplegament a producció: instància AWS EC2 amb el port 80 i 22 oberts al Security Group

---

## Instal·lació i posada en marxa

### 1. Clonar el repositori

git clone https://github.com/Xavi-H/examenDesplegament.git
cd examenDesplegament

### 2. Entorn de desenvolupament

Aixeca tots els serveis en segon pla:

docker compose up -d


Docker Compose fusiona automàticament docker-compose.yml i docker-compose.override.yml. Això construeix la imatge localment i activa el bind mount de ./src.


Accedeix a l'aplicació:
- Des d'un terminal local: http://localhost:8080
- Des d'un Codespace: obre la pestanya **Ports** i clica l'enllaç del port 8080


## Verificació que funciona correctament

### Verificar que els contenidors estan en marxa

docker compose ps

Resultat esperat: els dos contenidors (web i db) han d'estar en estat Up.