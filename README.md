# **1.** ✨ **1. INTRODUCCIÓN** ✨

En el presente documento se describe el desarrollo e implementación de soluciones basadas en **Salesforce☁️** para la organización **Construfurgo🏗️**. Este proyecto académico tiene como objetivo la optimización de los procesos internos de la empresa mediante la configuración y personalización de la plataforma Salesforce.

### 👨‍💻 **Rol como Salesforce Administrator**

Como **Salesforce Administrator**, mi rol incluye:

- ⚡ **Diseñar y configurar aplicaciones Lightning.**
- 📊 **Crear Dashboards y Reportes personalizados.**
- 🔄 **Desarrollar flujos de automatización** para mejorar la eficiencia operativa.
- 🧩 **Optimizar la toma de decisiones** mediante una gestión inteligente de los datos.

### 🎯 **Objetivos de la Implementación**

A través de esta implementación se busca:

- 📈 **Gestionar la información de forma eficiente**
- 👁️‍🗨️ **Visualizar datos clave** para la toma de decisiones
- 🤖 **Automatizar tareas repetitivas** y procesos operativos
- 💻 **Mejorar la experiencia del usuario** dentro de la plataforma Salesforce

# 2. 🛠️ **CONFIGURACIÓN DE LA ORGANIZACIÓN** 🛠️

El primer paso en nuestra implementación es definir la **configuración de la organización**, donde estableceremos información relevante de la compañía **Construfurgo** 🏗️, como horarios laborales, datos generales y personalización del dominio.

## ⏰ **Definir Horas Laborales**

Utilizando el buscador **Quick Find**, navegamos a:

> Company Settings → Business Hours

Aquí configuraremos las **horas laborales** de nuestra organización, lo cual es clave para gestionar correctamente procesos y automatizaciones en función del horario.

![Configuracion Horas Laborales](/Pantallazos/CompanyInformation/BussinesHours.PNG)

Configuracion Horas Laborales

*Configuración de Horas Laborales*

## 🏢 **Información General de la Organización**

A continuación, definiremos datos clave como:

- Nombre de la organización 🏷️
- Dirección 🗺️
- Ciudad 🏙️
- Zona horaria 🌍

Para ello, en el cuadro **Quick Find**, buscamos:

> Company Settings → Company Information

![Información General de la Organización](/Pantallazos/CompanyInformation/CompanyInformation.PNG)
*Información General de la Organización*

## 🌐 **Personalización del Dominio**

Finalmente, personalizaremos el dominio de nuestra organización para reflejar la identidad de **Construfurgo** y facilitar la gestión de acceso de usuarios.

En **Quick Find**, accedemos a:

> Company Settings → My Domain

![Personalizar Dominio](/Pantallazos/CompanyInformation/Domain.PNG)

*Personalizar Dominio*

# **3.** 🔐 **SEGURIDAD Y ACCESOS** 🔐

En esta sección se detalla cómo se configuró la seguridad y el acceso a los datos dentro de la organización **Construfurgo** 🏗️, garantizando que cada usuario tenga acceso únicamente a la información que necesita según su rol y perfil.

## 🧑‍💼 **Creación de Roles**

El cliente definió el siguiente **organigrama** y los **roles** correspondientes dentro de la compañía. Esto permite controlar **quién puede ver, editar y reportar registros** dentro de la organización:

![Jerarquia de Roles - ConstruFurgo](/Pantallazos/CreacionDeRoles/JerarquiaRoles.PNG)

🔎 **Principio de Visibilidad por Jerarquía:**

- Los usuarios pueden **ver, editar y reportar** sobre los datos creados por sus **subordinados**.
- El **CEO** 👨‍💼 tiene acceso a **todos los datos** de la organización, incluyendo los de todos los empleados.

## 🛠️ **Creación de Perfiles (Profiles)**

Se procedió a crear los **Profiles** definidos por la organización, basándonos en la información del archivo `.csv` proporcionado.

![Technical Support Profile](/Pantallazos/Security/TechnicalSupport.PNG)

### 🧹 **Limpieza de Permisos**

Se realizó una **limpieza de permisos a objetos** para los diferentes perfiles, dejando solo los permisos estrictamente necesarios.

![Technical Support Profile](/Pantallazos/Security/TechnicalSupportObjectPermissions.PNG)

✅ Es importante que los **tres perfiles creados estén limpios** antes de asignar los **Permission Sets** correspondientes a cada uno.

## 🗂️ **Distribución de Roles y Permisos**

A continuación, se presenta la tabla con la **distribución de objetos**, los **permisos** asignados por rol y los **campos accesibles** para cada uno.

### 📊 **Tabla de Permisos y Accesibilidad**

| **Rol** | **Objetos Accesibles** | **Permisos a Nivel de Objeto** | **Campos Clave Accesibles** |
| --- | --- | --- | --- |
| **Gerente de Compras y Logística** | Accounts, Contacts, Products, Cases | Leer/Editar | Todos los campos |
| **Coordinador de Logística** | Accounts, Products, Cases | Leer/Editar | Todos los campos |
| **Ejecutivo de Compras** | Products, Cases | Leer/Crear | Name, Category, Stock, Price (Products) / Subject, Priority (Cases) |
| **Gerente de Soporte Técnico** | Accounts, Contacts, Cases | Leer/Editar | Todos los campos |
| **Coordinador de Soporte** | Cases | Leer/Editar | Todos los campos |
| **Técnico de Ensamblaje** | Cases | Leer | Subject, Priority, Status |
| **Gerente de Ventas** | Leads, Opportunities, Accounts, Contacts, Products | Leer/Editar/Crear | Todos los campos |
| **Administrador de Ventas** | Leads, Opportunities, Accounts, Contacts, Products | Leer/Editar/Crear | Todos los campos |
| **Ejecutivo de Ventas** | Leads, Opportunities, Products | Leer/Crear | Name, Stage, Amount (Opportunities) / Name, Category (Products) |

## 🧩 **Tabla de Permission Sets** 🧩

En la siguiente tabla se presentan los diferentes **Permission Sets**, vinculados con su respectivo objeto, los permisos que habilitan, los roles asociados y los usuarios asignados.

📈 Aunque la organización aún no es grande, se proyecta un **crecimiento en los próximos trimestres**. Por ello, se diseñó una estructura granular de permisos, segmentando el acceso a los datos para **limitar visibilidad y reforzar la seguridad**.

| **🆔Permission Set Name** | **📦Object** | **🔐Object Permissions** | **🧑‍💼Roles** | **👤User** |
| --- | --- | --- | --- | --- |
| Construfurgo Compras Logistica Core | Accounts, Products, Cases | Read/Edit | Gerente Compras Logistica/Coordinador Logistica |  |
| Construfurgo Compras Logistica Manager | Contacts | Read/Edit | Gerente Compras Logistica |  |
| Construfurgo Compras Logistica Executive | Products, Cases | Read/Create | Ejecutivo de Compras |  |
| Construfurgo Soporte Tecnico Core | Cases | Read | Tecnico Ensamblaje | Ana Martinez |
| Construfurgo Coordinador Soporte | Cases | Read/Edit | Coordinador De Soporte |  |
| Construfurgo Gerente Soporte Tecnico | Accounts, Contacts, Cases | Read/Edit | Gerente de Soporte Tecnico |  |
| Construfurgo Ventas Core | Leads, Opportunities,Accounts, Contacts,Products | Read/Edit/Create | Gerente de Ventas/Administrador de Ventas | Maria Gomez |
| Construfurgo Ejecutivo Ventas | Leads, Opportunities, Products | Read/Create | Ejecutivo de Ventas | Fernando Morales |

# ⚙️ **Creación de Permission Sets**

A continuación, se detalla el proceso para **crear y configurar los Permission Sets** dentro de Salesforce:

1. Crear el **Permission Set** deseado.
2. Ingresar a la sección **Object Settings**.
3. Configurar los objetos que el permiso afectará, asignando permisos de **lectura**, **edición** y/o **creación**, según corresponda.

![Permission Set - Construfurgo Compras Logistica Core](/Pantallazos/Security/PermissionsSet1.PNG)

### 📂 **Ejemplo: Permisos sobre el Objeto Account**

En este ejemplo, se otorgan permisos de **lectura y edición** sobre el objeto **Account** a los usuarios que tengan asignado este Permission Set.

![Permissions Name - Construfurgo Compras Logistica Core](/Pantallazos/Security/PermissionSet2.PNG)

## 👥 **Asignación de Permisos a Usuarios**

Según lo establecido por el cliente, se seleccionaron **3 usuarios** del archivo `.csv` para asignarles permisos de acceso a objetos específicos.

🔸 **Ejemplo: Asignación del Permiso a Ana Martinez**

Rol: **Técnico de Ensamblaje** | Perfil: **Technical Support**

![Seleccion de Usuario](/Pantallazos/Security/AssignPermissionSet.PNG)

### 📅 **Asignación Temporal (Opcional)**

Se puede establecer una **fecha de expiración** para que el permiso deje de aplicarse automáticamente.

➡️ En este caso, **no se aplicará fecha de expiración**.

📸 **Paso 2: Revisión y Confirmación de Asignación**

![Revision y Asignacion del Permiso](/Pantallazos/Security/AssignPermissionSet2.PNG)

## 🛡️ **Conclusión: Seguridad como Pilar Estratégico**

La **seguridad en Salesforce** es clave para garantizar la **integridad, confidencialidad y disponibilidad** de la información en la organización.

A través de herramientas como:

- 🔐 **Perfiles**
- 🧩 **Permission Sets**
- 🧑‍💼 **Jerarquía de Roles**

Salesforce permite un **control granular y eficiente** sobre **quién puede acceder, visualizar y modificar** datos críticos del negocio.

## 🚀 **Beneficios de una Buena Gestión de Seguridad:**

- 🔒 Protección de datos
- 📉 Reducción de riesgos de acceso no autorizado
- ✅ Cumplimiento de normativas y políticas internas
- 📊 Confianza, rendimiento y escalabilidad en el negocio

# 4.**🧩🤖FLOWS Y AUTOMATIZACION🧩🤖**

La **automatización de procesos** es clave para mejorar la eficiencia en la organizacion, reducir errores humanos y garantizar una experiencia fluida para clientes y empleados. Dentro de Salesforce, los **Flows** (o Flujos) se convierten en una herramienta estratégica fundamental, ya que permiten **automatizar tareas complejas**, sin necesidad de escribir código, mediante un enfoque visual y flexible.

Los **Flows** permiten a las organizaciones:

- 🔄 **Optimizar procesos repetitivos** como la asignación de tareas, envíos de correos automáticos, actualizaciones de registros y más.
- 🔍 **Estandarizar flujos de trabajo**, asegurando que los procesos críticos se realicen de manera consistente y sin omisiones.
- 🚀 **Acelerar la toma de decisiones**, al facilitar el acceso a datos actualizados y automatizar acciones en tiempo real.
- 🧩 **Adaptarse rápidamente al cambio**, modificando procesos de negocio de manera ágil ante nuevas necesidades sin depender completamente del equipo de desarrollo.

## Crear un Flow (Automatizacion)

Buscar en el cuadro de busqueda **Quick Find —> Flows** y seleccionar esta opcion:

- Seleccionar **Start From Scratch**
- Siguiente **Record Triggered Flow -** Esta opcion permite que se inicie el flujo cuando se crea, edita o elimina algun record.

![Seleccionar tipo de Flow](/Pantallazos/Flows/Flows2.PNG)

Seleccionar tipo de Flow

## ⚙️ **Configuración del Inicio del Flujo (Configure Start)**

La configuración inicial del flujo automático **Record-Triggered Flow**, el cual se ejecuta automáticamente cuando ocurre un cambio específico en un registro.

### Objeto Relacionado al Flujo

- **Objeto:** `LeadC`
El flujo está vinculado al objeto personalizado **LeadC**, lo que indica que cualquier modificacion en este flujo será aplicada sobre los registros de dicho objeto.

### Disparador del Flujo (Configure Trigger)

- **Trigger the Flow When:**
    - ✅ **A record is updated**
    El flujo se activará automáticamente **cuando un registro del objeto LeadC sea actualizado**.

### Condiciones de Entrada (Set Entry Conditions)

- **Condition Requirements:** `None`
Actualmente, no se han definido condiciones específicas para limitar la ejecución del flujo. Esto significa que **el flujo se ejecutará con cada actualización** en cualquier campo del objeto LeadC.

### Optimización del Flujo (Optimize the Flow for)

- **Actions and Related Records**
Esta opción permite al flujo **actualizar cualquier registro relacionado, enviar correos electrónicos u otras acciones** después de que el registro principal haya sido guardado en la base de datos.

![Configurar Inicio](/Pantallazos/Flows/Flows3.PNG)

Configurar Inicio

## 🔀 **Lógica de Decisión en el Flujo: "Interacción más de 3 veces"**

En esta parte del flujo se evalúa una condición específica para **tomar una decisión** que determine el camino que seguirá el proceso automático.

### 🧩 **Configuración del Elemento Decision**

- **Label:** `Interaccion mas de 3 veces`
- **API Name:** `Interaccion_mas_de_3_veces`

### 📊 **Resultados Posibles (Outcomes)**

1. **Opción 1: Mayor a 2**
    - **Label:** `Mayor a 2`
    - **API Name:** `Mayor_a_2`
    - **Condición:**
        - **Recurso Evaluado:** `Triggering LeadC__c > Counter`
        - **Operador:** `Greater Than or Equal` (Mayor o igual)
        - **Valor:** `2`
    
    **Interpretación:**
    
    Si el contador de interacciones del Lead es **mayor o igual a 2**, el flujo seguirá por este camino.
    
    - **Acciones que se ejecutan:**
        1. Se crea una oportunidad.
        2. Se elimina el Lead.
        3. Fin del flujo.
2. **Opción 2: Menor a 2**
- Esta ruta se ejecuta **si no se cumple** la condición de la opción "Mayor a 2", es decir, si el contador es **menor a 2**.
- **Acciones que se ejecutan:**
    1. Se asigna un nuevo valor al contador de interacciones.
    2. Se actualiza el registro Lead.
    3. Fin del flujo.

### ⏰ **Momento de Ejecución de la Decisión**

- **When to Execute Outcome:**
    - ✅ `If the condition requirements are met`
    Esto asegura que la decisión se toma **inmediatamente al cumplirse la condición evaluada**.

![Configuracion de Decision](/Pantallazos/Flows/Flows4.PNG)

Configuracion de Decision

## ➕ **Configuración del Nodo "Generar Oportunidad" – Create Records**

Este componente se activa cuando el flujo toma el camino **"Mayor a 2"** en la decisión, es decir, cuando un Lead ha tenido **2 o más interacciones**. Su función es **crear una nueva oportunidad** relacionada con ese Lead.

### ⚙️ **Parámetros de Configuración**

- **Tipo de Componente:** `Create Records`
- **Nombre del Nodo:** `Generar Oportunidad`
- **Método de Asignación de Valores:**
    - `Manually` (Manual)
    Permite establecer manualmente los valores de los campos que se asignarán al nuevo registro.

### 📂 **Objeto a Crear**

- **Objeto Salesforce:** `OpportunityC`
Es un objeto personalizado (nota el sufijo `C`), utilizado para almacenar oportunidades relacionadas con posibles ventas.

### 📝 **Asignación de Valores de Campos**

1. **Campo:** `Name`
    - **Valor Asignado:** `Triggering LeadC__c > Name`
        - Este valor toma el **nombre del Lead que activó el flujo** y lo asigna como **nombre de la nueva oportunidad**.
2. **Campo:** `Stage`
    - **Valor Asignado:** `Prospeccion`
        - Define que la oportunidad se encuentra en la etapa inicial del ciclo de ventas: **Prospección**.

### 🔍 **Check for Matching Records**

- **Estado:** `Deshabilitado`
No se está buscando registros duplicados ni haciendo validación previa. Se crea la oportunidad **sin verificar coincidencias**.

![Create Record - Generar Oportunidad](/Pantallazos/Flows/Flows5.PNG)

Create Record - Generar Oportunidad

## 🗑️ **Configuración del Nodo "Eliminar Lead" – Delete Records**

Este componente se ejecuta **inmediatamente después de la creación de la oportunidad**, como parte de la ruta del flujo que maneja Leads con **2 o más interacciones**. Su función es eliminar el Lead que originó la ejecución del flujo.

### ⚙️ **Parámetros de Configuración**

- **Tipo de Componente:** `Delete Records`
- **Etiqueta (Label):** `Eliminar Lead`
- **Nombre API:** `Eliminar_Lead`

### 🔍 **Método para Encontrar los Registros a Eliminar**

- **Opción Seleccionada:** `Use the IDs stored in a record variable or record collection variable`
Esto significa que se eliminará un registro **específico** basado en su ID, el cual ya está disponible como variable en el flujo.

### 📝 **Registro a Eliminar**

- **Variable:** `Triggering LeadC__c`
Representa el Lead personalizado que **disparó la ejecución del flujo**.
Al estar directamente vinculado al evento de activación, ya contiene el **ID necesario** para su eliminación.

### 🧠 **Resumen de la Lógica**

1. Una vez creada la oportunidad a partir de un Lead con ≥2 interacciones, este nodo:
    - **Elimina el Lead original** del sistema.
    - Ayuda a **depurar la base de datos**, evitando duplicidad y manteniendo solo registros activos como oportunidades.
2. **Motivo Estratégico:**
    
    Al eliminar el Lead después de convertirlo en una oportunidad, se sigue un flujo natural del proceso de ventas, **transformando Leads calificados en oportunidades** y eliminando información redundante.
    
    ![Delete Record ](/Pantallazos/Flows/Flows6.PNG)
    
    Delete Record 
    

## ➕ **Configuración del Nodo "Contador de Interacción" – Assignment**

Este bloque se encarga de **incrementar el número de interacciones** que ha tenido un Lead cuando todavía no supera las 3 interacciones.

### ⚙️ **Parámetros de Configuración**

- **Tipo de Componente:** `Assignment`
- **Etiqueta (Label):** `Contador de Interacción`
- **Nombre API:** `Contador_de_Interaccion`

### 🧮 **Valor Asignado**

- **Variable:** `Triggering LeadC__c > Counter`
    
    Se refiere al campo personalizado `Counter` dentro del Lead que activó el flujo. Este campo registra el número de veces que hubo una interacción con dicho Lead.
    
- **Operador:** `Add`
- **Valor:** `1`

### 🔄 **¿Qué hace este nodo?**

1. **Toma el valor actual** del campo `Counter` del Lead.
2. **Le suma 1**, indicando que se ha producido una nueva interacción.
3. El resultado **se guarda nuevamente en el mismo campo `Counter`**.

### 📈 **Propósito Estratégico**

Este Assignment **lleva el control de la cantidad de interacciones** que se ha tenido con cada Lead. Es esencial para que, en ejecuciones futuras del flujo, la decisión de **mayor o menor a 2 interacciones** se tome con base en datos actualizados.

### 

![Contador de Interaccion ](/Pantallazos/Flows/Flows7.PNG)

Contador de Interaccion 

## 📝 **Nodo: Update Records 1**

### ⚙️ **Propósito:**

Actualizar el valor del campo `Counter__c` en el registro del Lead que activó el flujo, **después** de que este valor fue incrementado en el nodo anterior (Assignment).

### 📋 **Configuración Detallada**

| Parámetro | Valor |
| --- | --- |
| **Label** | `Update Records 1` |
| **API Name** | `Update_Records_1` |
| **How to Find Records to Update** | `Use the LeadC record that triggered the flow` |
| **Condition Requirements** | `None—Always Update Record` (se actualiza sin condiciones adicionales) |
| **Field to Update** | `Counter__c` |
| **New Value** | `$Record > Counter` (que ya fue incrementado en el Assignment) |

### 🔄 **¿Qué hace exactamente este nodo?**

1. **Toma el registro del Lead** que inició el flujo (triggered the flow).
2. **Actualiza su campo personalizado `Counter__c`**, asignándole el nuevo valor incrementado que se calculó en el nodo anterior.
3. **Guarda el cambio** en Salesforce, asegurando que el contador se mantenga actualizado para futuras ejecuciones del flujo.

### 🔗 **Relación con el Assignment:**

- En el **Assignment**, se incrementa el valor de `Counter__c` pero **solo en memoria** dentro del flujo.
- En **Update Records 1**, se **persiste ese nuevo valor** en la base de datos de Salesforce, escribiéndolo directamente en el registro del Lead.

![Update Records](/Pantallazos/Flows/Flows8.PNG)