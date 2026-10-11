# config-server-grupoA

Spring Cloud Config Server - Grupo A
(Spring Boot 4.1.1, Spring Cloud 2025.1.3, Java 25)

## Datos generales
- Puerto: 8888
- Repo de configuración: https://github.com/LeitoDLight/config-repo-grupoA
- Rama: main
- Archivos que sirve: pedido-service-dev.properties y pedido-service-prod.properties

## Cómo ejecutarlo
1. Clonar este repositorio y abrirlo en IntelliJ (JDK 25).
2. Ejecutar ConfigServerGrupoAApplication.
3. Requiere internet: al arrancar clona el repo de configuración desde GitHub.

## Orden de arranque
1. config-server-grupoA (8888)
2. discovery-server-grupoA (8761)
3. pedido-service-grupoA (8071)
4. pago-service-grupoA (8072)
5. api-gateway-grupoA (8070)

## Cómo probar
- http://localhost:8888/pedido-service/dev -> monto-minimo-envio-gratis = 150.00
- http://localhost:8888/pedido-service/prod -> monto-minimo-envio-gratis = 300.00

## Configuración que usa pedido-service-grupoA
    spring.application.name=pedido-service-grupoA
    spring.profiles.active=dev
    spring.config.import=configserver:http://localhost:8888
    spring.cloud.config.name=pedido-service
    management.endpoints.web.exposure.include=refresh,health,info

`spring.cloud.config.name=pedido-service` es necesario porque el nombre de la aplicación lleva el sufijo -grupoA, pero los archivos se llaman pedido-service-{perfil}.properties.

## Prueba de recarga en caliente
1. GET http://localhost:8070/api/v1/pedidos/configuracion -> 150.00
2. Editar en GitHub pedido-service-dev.properties a 250.00 (commit)
3. POST http://localhost:8071/actuator/refresh
4. GET http://localhost:8070/api/v1/pedidos/configuracion -> 250.00 (sin reiniciar)
5. Devolver a 150.00

## Integrantes - Grupo A
| Integrante | Código | Responsabilidad |
|---|---|---|
| Leonardo Dorregaray Guevara | I201924621 | 2.2 Config Server (config-server-grupoA y config-repo-grupoA) |
| Alberto Muzaurieta Hidalgo | I201623265 | 2.3 Consumo en pedido-service y 2.4 Recarga dinámica |
