# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 2 - Modelo de Información y Diagrama de Contexto_

## 👥 Integrantes del equipo
- David Santiago Medina (davidmebu@unisabana.edu.co)
- Santiago Navarro (santiagonacu@unisabana.edu.co)
- Jacobo Pacheco (jacobopama@unisabana.edu.co)
- Juan Diego Martínez (juandmaes@unisabana.edu.co)

## 🧠 Descripción general del trabajo

El objetivo del taller fue analizar la estructura de información utilizada por la empresa en el proceso de **atención de pacientes para empresas**, y representarla mediante un modelo de datos que permitiera identificar claramente las entidades, sus atributos y las relaciones existentes entre ellas. A través de este proceso se buscó comprender cómo se organiza la información dentro del sistema y cómo puede modelarse utilizando diagramas Entidad-Relación.

## 🔧 Proceso de desarrollo

Para la realización del trabajo se inició con el análisis de la estructura de datos utilizada por la empresa, con el propósito de identificar la información principal y comprender cómo se relacionaban los distintos elementos del sistema. A partir de este análisis se definieron las entidades, atributos y relaciones necesarias para representar el funcionamiento del proceso.

En una primera fase se utilizó la herramienta Mermaid, donde se elaboró un diagrama entidad-relación orientado a tablas, permitiendo organizar inicialmente las entidades junto con sus atributos, claves primarias y claves foráneas. Este paso facilitó la validación de la estructura lógica de la base de datos y la identificación de las relaciones y cardinalidades entre las tablas.

Posteriormente, con la estructura ya definida, se procedió a construir el modelo Entidad-Relación conceptual en la plataforma SmartDraw, empleando la notación clásica mediante rectángulos para entidades, rombos para relaciones y óvalos para atributos. En esta etapa se trasladó y ajustó la información del diagrama inicial, refinando las cardinalidades y la representación conceptual del modelo.

## 🧩 Análisis del modelo propuesto

### 1. Cómo se estructura el modelo entregado

El diagrama y el modelo Entidad-Relación entregado se estructuran inicialmente a partir de las entidades **Empresa** y **Paciente**, las cuales se relacionan con la entidad **Concepto Médico**. Esta relación se definió debido a que cada concepto médico solo puede pertenecer a un paciente y estar asociado a una única empresa. Sin embargo, tanto una empresa como un paciente pueden tener múltiples conceptos médicos asociados. En el caso de las empresas, esto ocurre porque los procesos de contratación o renovación laboral involucran a varias personas, mientras que un paciente puede generar distintos conceptos médicos debido a renovaciones periódicas o evaluaciones requeridas de manera independiente.

El **Concepto Médico** puede incluir uno o varios servicios detallados, tales como consulta ocupacional, optometría, audiología, psicología o laboratorio clínico. Por esta razón se creó la entidad **Servicios_Detallado**, modelada como una entidad débil, cuya función es relacionar los servicios ofrecidos por la IPS con los profesionales que los realizan y con el concepto médico correspondiente. Cada servicio detallado pertenece a un único concepto médico, a un solo tipo de servicio y a un único profesional, permitiendo además registrar los resultados y observaciones del examen realizado.

Asimismo, se definió que un servicio puede aparecer en cero o múltiples servicios detallados, al igual que un profesional puede participar en varios registros dependiendo de las evaluaciones realizadas.

---

### 2. Cómo representa las necesidades del cliente

El modelo representa las necesidades del cliente al permitir llevar un registro organizado de todos los pacientes atendidos, junto con sus respectivos exámenes médicos y conceptos generados. Además, estos registros pueden asociarse a una empresa específica, lo que facilita la gestión de procesos relacionados con contratación, seguimiento ocupacional y renovaciones laborales.

De esta manera, la estructura propuesta permite consultar información médica, profesional y empresarial de forma integrada, apoyando la trazabilidad de los servicios prestados por la IPS.

---

### 3. Qué supuestos se tomaron

Durante el proceso de modelado se establecieron ciertos supuestos. Debido a que **Biofile** es un software de terceros, no se tiene acceso directo a la estructura real de la base de datos utilizada por la herramienta. Por esta razón, el modelo fue construido a partir de los datos y procesos conocidos por la empresa, buscando representar una estructura lógica que se aproxime al funcionamiento real del sistema.

En consecuencia, algunas decisiones de diseño se basaron en la interpretación del flujo operativo y en la información disponible, asumiendo que la organización de los datos sigue una lógica similar a la planteada en el modelo propuesto.



## 📈 Diagrama final entregado
<img width="6332" height="5065" alt="Healthcare Entity-2026-02-20-224701" src="https://github.com/user-attachments/assets/438102c3-3506-4c77-a481-40e25941ec73" />
<img width="1828" height="1075" alt="Screenshot 2026-02-20 174826" src="https://github.com/user-attachments/assets/869efa58-72cb-4ccd-a6ad-fd462a3f7f19" />


## 📋 Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Empresa | Entidad | Organización que solicita la atención médica ocupacional para sus trabajadores y a cuyo nombre se generan los conceptos médicos. | Empresa cliente |
| Paciente |Entidad | Persona que recibe la atención médica y a quien se le realizan los exámenes y evaluaciones ocupacionales. | Paciente |
| Profesional |Entidad | Personal de salud encargado de realizar los servicios médicos y registrar los resultados de los exámenes. | Profesional de salud |
| Concepto_Medico | Entidad | Registro que agrupa la evaluación médica ocupacional de un paciente, asociada a una empresa específica. | IPS / Área médica |
| Servicio | Entidad | Tipo de examen o evaluación ofrecida por la IPS (ocupacional, optometría, audiometría, laboratorio, etc.). | IPS |
| Servicios_detallado | Entidad débil / Componente | Registro detallado de cada servicio realizado dentro de un concepto médico, incluyendo profesional, resultados y observaciones. | Profesional de salud |

## 🔍 Investigación complementaria
### Tema investigado:
Relación de FHIR con los modelos entidad-relación

### Resumen:
El estándar FHIR (Fast Healthcare Interoperability Resources) de HL7 define una estructura formal para modelar información clínica y administrativa en sistemas de salud. FHIR propone “recursos” estandarizados como Organization, Patient, Practitioner, ServiceRequest, Observation y DiagnosticReport, que representan organizaciones, pacientes, profesionales, solicitudes de servicios, resultados individuales e informes diagnósticos agrupados. Este estándar no solo define entidades, sino también sus relaciones y reglas de interoperabilidad (HL7, 2019).

La relación con el caso desarrollado es directa: la entidad Empresa se alinea con Organization; Paciente con Patient; Profesional con Practitioner; Servicios_detallado se asemeja a Observation (resultado individual con responsable); y Concepto_Medico cumple un rol similar a DiagnosticReport, que agrupa múltiples resultados bajo un mismo informe. Además, FHIR respalda la buena práctica de separar orden del servicio (ServiceRequest), resultado atómico (Observation) e informe final (DiagnosticReport), lo que fortalece conceptualmente el modelo ER propuesto y justifica su estructura desde un estándar internacional.

## 📚 Referencias
- [1] Health Level Seven International (HL7). (2019). FHIR Release 4 (R4) Specification. https://hl7.org/fhir/R4/
- [2] Fuente asistida por IA: ChatGPT, febrero 2026.

---

_Este documento hace parte de la entrega del taller 2 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
