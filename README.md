# 💰 AWS Cost Analysis & Remediation – Cost Explorer

Proyecto enfocado en el análisis de costos en AWS utilizando AWS Cost Explorer y la aplicación de remediaciones técnicas para optimizar gastos en la nube.

📍 Región analizada: Global (Cost Explorer es servicio global)  
🎯 Enfoque: Optimización, visibilidad y remediación

---

## 🎯 Objetivo

- Identificar servicios con mayor consumo
- Detectar recursos subutilizados
- Analizar tendencias de gasto
- Aplicar remediaciones técnicas
- Implementar buenas prácticas FinOps

---

# 🏗️ Arquitectura Conceptual

<p align="center">
  <img src="images/cost-analysis-architecture.png" width="900">
</p>

---

# 🧩 Paso 1 – Habilitar AWS Cost Explorer

1. Ir a AWS Console
2. Buscar: Billing
3. Seleccionar: Cost Explorer
4. Click en:
   Enable Cost Explorer

⚠️ Puede tardar hasta 24 horas en mostrar datos iniciales.

---

# 🧩 Paso 2 – Analizar Costos por Servicio

Ir a:

Cost Explorer → Reports

Configurar:

- Date Range: Last 30 days
- Granularity: Monthly
- Group by: Service

Identificar:

- EC2
- RDS
- S3
- NAT Gateway
- Data Transfer
- EBS

---

# 🧩 Paso 3 – Analizar Costos por Región

Configurar:

- Group by: Region

Objetivo:

- Detectar recursos en regiones no utilizadas
- Identificar duplicación de infraestructura

---

# 🧩 Paso 4 – Analizar Costos por Tag

Configurar:

- Group by: Tag
- Seleccionar tag como:
  Environment
  Project
  Owner

Esto permite:

- Identificar recursos sin etiquetar
- Detectar equipos con mayor consumo
- Aplicar gobernanza

---

# 🧩 Paso 5 – Identificar Recursos Costosos

Servicios comunes con alto impacto:

## EC2

- Instancias sobredimensionadas
- Instancias en estado running innecesariamente
- Volúmenes EBS no utilizados

## RDS

- Bases de datos activas fuera de horario laboral
- Instancias con tamaño elevado
- Backups excesivos

## S3

- Objetos sin lifecycle policy
- Datos en clase Standard innecesariamente

## NAT Gateway

- Alto costo mensual fijo
- Uso innecesario en entornos pequeños

---

# 🛠 Paso 6 – Aplicar Remediaciones Técnicas

## 🔹 EC2

- Detener instancias fuera de horario
- Cambiar tipo de instancia (Rightsizing)
- Eliminar volúmenes EBS no asociados
- Comprar Savings Plans (si aplica)

---

## 🔹 RDS

- Implementar auto stop/start con Lambda
- Reducir tamaño de instancia
- Evaluar migración a Aurora Serverless
- Ajustar retención de backups

---

## 🔹 S3

- Aplicar Lifecycle Policy
- Mover datos a:
  - S3 Standard-IA
  - Glacier
  - Glacier Deep Archive

---

## 🔹 NAT Gateway

- Evaluar uso de:
  - NAT Instance
  - VPC Endpoints
  - Arquitectura privada optimizada

---

# 📊 Paso 7 – Crear Presupuestos (Budgets)

Ir a:

Billing → Budgets → Create Budget

Configurar:

- Cost Budget
- Monthly threshold
- Alert via Email
- Alert via SNS

Esto permite:

- Notificación temprana
- Control proactivo de gasto

---

# 📈 Paso 8 – Monitoreo Continuo

Recomendaciones:

- Revisar Cost Explorer semanalmente
- Implementar tagging obligatorio
- Automatizar apagado de entornos Dev
- Habilitar Cost Anomaly Detection

---

# 🔐 Buenas Prácticas Aplicadas

- Principio de mínimo privilegio
- Gobierno mediante tags
- Automatización de recursos no productivos
- Optimización basada en datos reales
- Cultura FinOps

---

# 💰 Impacto Esperado

- Reducción de 20–60% en entornos Dev/Test
- Mejor visibilidad financiera
- Eliminación de recursos huérfanos
- Optimización de arquitectura

---

# 🛠 Servicios Utilizados

- AWS Cost Explorer
- AWS Budgets
- Amazon EC2
- Amazon RDS
- Amazon S3
- AWS Lambda
- Amazon SNS

