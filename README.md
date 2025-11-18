# **CartonCaps Referral API**

**Descripción:**  
Breve descripción del proyecto, qué hace y tecnologías principales.

---

## **Índice**
1. [Arquitectura del Proyecto](#arquitectura-del-proyecto)
2. [Endpoints](#endpoints)
3. [Flujo de Referidos](#flujo-de-referidos)
4. [Anti-abuso](#anti-abuso)
5. [Pruebas Unitarias](#pruebas-unitarias)
6. [Cómo Correr el Proyecto](#cómo-correr-el-proyecto)
7. [Tecnologías Utilizadas](#tecnologías-utilizadas)

---

## **Arquitectura del Proyecto**
- **CartonCaps.Api:** Controllers, Program.cs, appsettings.json  
- **CartonCaps.Application:** DTOs, Interfaces, Services, Validators  
- **CartonCaps.Domain:** Entities  
- **CartonCaps.Infrastructure:** Data, Repositories, MockData  
- **CartonCaps.Common:** Middleware  
- **CartonCaps.Tests:** Pruebas unitarias  

Diagrama de flujo de dependencias:
[Web API] → [Application] → [Domain] → [Infrastructure]

---

## **Endpoints**
### Registrar visita / Redirect
`POST /api/referralsVisit/redirect?referralCode={referralCode}`  
- Obtiene IP del visitante  
- Valida visitas recientes  
- Registra visita si corresponde  
- Redirige a URL configurada  

### Historial de visitas
`GET /api/referralsVisit/referralVisitHistory`  
- Devuelve listado de visitas registradas  
- Ordenadas por fecha  

---

## **Flujo de Referidos**
1. Usuario solicita enlace de invitación  
2. Enlace contiene `referralCode`  
3. Usuario comparte enlace  
4. Usuario invitado hace clic → `/referralsVisit/redirect`  
5. Registro de visita y redirección  
6. Deferred deep link completa navegación dentro de la app  

---

## **Anti-abuso**
- Validación de clicks únicos por IP  
- Registro sin interrumpir redirección  
- Logging de casos ignorados  

---

## **Pruebas Unitarias**
- Creación de referral  
- Redirección con IP bloqueada  
- Error por referral code inexistente  
- Mapeo correcto a DTOs  

---

## **Cómo Correr el Proyecto**
1. Clonar repo  
2. Abrir solución en VS Code o Visual Studio  
3. Restaurar paquetes NuGet  
4. Ejecutar `CartonCaps.Api`  
5. Acceder a Swagger  

---

## **Tecnologías Utilizadas**
- .NET Core 6  
- Entity Framework InMemory  
- AutoMapper  
- Moq & xUnit & FluentAssertions  
- Swagger  
