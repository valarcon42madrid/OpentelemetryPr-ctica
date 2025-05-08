# Enunciado: (Modulo_OpenTel...)

# Carpeta descargada + carpeta docker-compose/ añadida para la realización (SampleFlask)

# Instrucciones para replicar y CAPTURAS pedidas (capturasYpasos)

Instrucciones para replicarlo:

-LEVANTAR TODO MENOS FLASK:
 docker-compose up -d

cd docker-compose/

 docker-compose up -d

-PREPARAR PYHTON:

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
opentelemetry-bootstrap --action=install


-IDENTIFICARSE PARA BASE DE DATOS:

export MONGO_URI="mongodb://root:examplepwd@localhost:27017/?authSource=admin"

-LEVANTAR SAMPLE-FLASK EN SEGUNDO PLANO Y GUARDANDO LOGS:

cd ..

nohup python app.py > docker-compose/app.log 2>&1 &


-EN localhost:3000 (interfaz-grafana) añadir datasources:
Jaeger|    http://jaeger:16686	     Loki|     http://loki:3100	   Prometheus| http://prometheus:9090

*Notas: si no se recibe nada con loki reiniciar empezando por promtail (en docker-compose/):
docker-compose down 
docker-compose up -d promtail
docker-compose up -d



* sí, dejo un .venv en sampleFlask; es aposta y no un despiste 
