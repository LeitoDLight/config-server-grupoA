# config-server-grupoA

Spring Cloud Config Server - Grupo A
(Spring Boot 4.1.1, Spring Cloud 2025.1.3, Java 25)

- Puerto: 8888
- Repo de configuración: https://github.com/LeitoDLight/config-repo-grupoA
- Archivos: pedido-service-dev.properties y pedido-service-prod.properties
- Orden de arranque:
  1. config-server-grupoA
  2. discovery-server-grupoA
  3. pedido-service-grupoA
  4. pago-service-grupoA
  5. api-gateway-grupoA
- Pruebas:
  - http://localhost:8888/pedido-service/dev
  - http://localhost:8888/pedido-service/prod
"@ | Set-Content -Encoding utf8 README.md

git add .
git commit -m "Config server grupo A"
git remote add origin https://github.com/LeitoDLight/config-server-grupoA.git
git push -u origin main
