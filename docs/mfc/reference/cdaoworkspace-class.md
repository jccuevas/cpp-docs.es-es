---
title: "CDaoWorkspace Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoWorkspace"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoWorkspace class"
  - "DAO workspaces [C++]"
  - "DAO workspaces [C++], CDaoWorkspace class"
  - "database engine [C++], accessing via workspace"
  - "DDLs [C++]"
  - "default workspaces [C++]"
  - "default workspaces [C++], DAO"
  - "valores predeterminados [C++], áreas de trabajo"
  - "clases ODBC [C++], vs. DAO classes"
  - "persistence [C++], DAO workspace"
  - "security [MFC]"
  - "security [MFC], DAO workspaces"
  - "sessions [C++], DAO workspace"
  - "transaction spaces [C++]"
  - "transaction spaces [C++], DAO workspace"
  - "Workspace class"
  - "workspaces [C++], DAO"
  - "workspaces [C++], default"
  - "workspaces [C++], interface to database engine"
  - "workspaces [C++], persistencia"
  - "Workspaces collection"
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoWorkspace Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Administra una sesión denominada, protegida mediante contraseña de la base de datos de inicio de sesión a cerrar la sesión, por un único usuario.  
  
## Sintaxis  
  
```  
class CDaoWorkspace : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoWorkspace::CDaoWorkspace](../Topic/CDaoWorkspace::CDaoWorkspace.md)|Construye un objeto del área de trabajo.  Después, llamada **Crear** o **Abrir**.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoWorkspace::Append](../Topic/CDaoWorkspace::Append.md)|Anexa un área de trabajo creada recientemente a la colección de áreas de trabajo del motor de base de datos.|  
|[CDaoWorkspace::BeginTrans](../Topic/CDaoWorkspace::BeginTrans.md)|Inicia una nueva transacción, que se aplica a todas las bases de datos abierto en el área de trabajo.|  
|[CDaoWorkspace::Close](../Topic/CDaoWorkspace::Close.md)|Cierre el área de trabajo y todos los objetos que contiene.  Pendientes transacciones es la revierte.|  
|[CDaoWorkspace::CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md)|completa la transacción actual y guarda los cambios.|  
|[CDaoWorkspace::CompactDatabase](../Topic/CDaoWorkspace::CompactDatabase.md)|compacta \(o duplicados\) una base de datos.|  
|[CDaoWorkspace::Create](../Topic/CDaoWorkspace::Create.md)|Crea un nuevo objeto de área de trabajo de DAO.|  
|[CDaoWorkspace::GetDatabaseCount](../Topic/CDaoWorkspace::GetDatabaseCount.md)|Devuelve el número de objetos de base de datos de DAO en la colección de bases de datos del área de trabajo.|  
|[CDaoWorkspace::GetDatabaseInfo](../Topic/CDaoWorkspace::GetDatabaseInfo.md)|Devuelve información sobre una base de datos especificada de DAO definido en la colección de bases de datos del área de trabajo.|  
|[CDaoWorkspace::GetIniPath](../Topic/CDaoWorkspace::GetIniPath.md)|Devuelve la ubicación de los valores de inicialización del motor de base de datos Microsoft Jet en el Registro de Windows.|  
|[CDaoWorkspace::GetIsolateODBCTrans](../Topic/CDaoWorkspace::GetIsolateODBCTrans.md)|Devuelve un valor que indica si las varias transacciones que implican el mismo origen de datos ODBC se aíslan a través de varias conexiones forzadas al origen de datos.|  
|[CDaoWorkspace::GetLoginTimeout](../Topic/CDaoWorkspace::GetLoginTimeout.md)|Devuelve el número de segundos antes de que se produzca un error cuando el usuario intenta iniciar una sesión en una base de datos ODBC.|  
|[CDaoWorkspace::GetName](../Topic/CDaoWorkspace::GetName.md)|Devuelve el nombre definido por el usuario para el objeto del área de trabajo.|  
|[CDaoWorkspace::GetUserName](../Topic/CDaoWorkspace::GetUserName.md)|Devuelve el nombre de usuario especificado cuando el área de trabajo creada.  Es el nombre del propietario del área de trabajo.|  
|[CDaoWorkspace::GetVersion](../Topic/CDaoWorkspace::GetVersion.md)|Devuelve una cadena que contiene la versión del motor de base de datos asociado al área de trabajo.|  
|[CDaoWorkspace::GetWorkspaceCount](../Topic/CDaoWorkspace::GetWorkspaceCount.md)|Devuelve el número de objetos del área de trabajo de DAO en la colección de áreas de trabajo del motor de base de datos.|  
|[CDaoWorkspace::GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md)|Devuelve información sobre un área de trabajo especificada de DAO definido en la colección de áreas de trabajo del motor de base de datos.|  
|[CDaoWorkspace::Idle](../Topic/CDaoWorkspace::Idle.md)|Permite que el motor de base de datos realizar tareas en segundo plano.|  
|[CDaoWorkspace::IsOpen](../Topic/CDaoWorkspace::IsOpen.md)|Devuelve cero si el área de trabajo está abierto.|  
|[CDaoWorkspace::Open](../Topic/CDaoWorkspace::Open.md)|Explícitamente abre un objeto del área de trabajo asociado al área de trabajo predeterminada de DAO.|  
|[CDaoWorkspace::RepairDatabase](../Topic/CDaoWorkspace::RepairDatabase.md)|Intenta reparar una base de datos dañada.|  
|[CDaoWorkspace::Rollback](../Topic/CDaoWorkspace::Rollback.md)|Finaliza la transacción actual y no guarda los cambios.|  
|[CDaoWorkspace::SetDefaultPassword](../Topic/CDaoWorkspace::SetDefaultPassword.md)|Establece la contraseña que el motor de base de datos utiliza cuando un objeto del área de trabajo se crea sin contraseña concreta.|  
|[CDaoWorkspace::SetDefaultUser](../Topic/CDaoWorkspace::SetDefaultUser.md)|Establece el nombre de usuario que el motor de base de datos utiliza cuando un objeto del área de trabajo se crea sin un nombre de usuario.|  
|[CDaoWorkspace::SetIniPath](../Topic/CDaoWorkspace::SetIniPath.md)|Establece la ubicación de los valores de inicialización del motor de base de datos Microsoft Jet en el Registro de Windows.|  
|[CDaoWorkspace::SetIsolateODBCTrans](../Topic/CDaoWorkspace::SetIsolateODBCTrans.md)|Especifica si las varias transacciones que implican el mismo origen de datos ODBC están aisladas fuerza varias conexiones al origen de datos.|  
|[CDaoWorkspace::SetLoginTimeout](../Topic/CDaoWorkspace::SetLoginTimeout.md)|Establece el número de segundos antes de que se produzca un error cuando el usuario intenta iniciar sesión en un origen de datos ODBC.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoWorkspace::m\_pDAOWorkspace](../Topic/CDaoWorkspace::m_pDAOWorkspace.md)|Señala al objeto subyacente del área de trabajo de DAO.|  
  
## Comentarios  
 En la mayoría de los casos, no necesitará varias áreas de trabajo, y no necesitará crear objetos explícitos del área de trabajo; al abrir base de datos y los objetos de conjunto de registros, utilizan el área de trabajo predeterminada de DAO.  Sin embargo, si es necesario, puede ejecutar varias sesiones al mismo tiempo crear objetos adicionales del área de trabajo.  Cada objeto del área de trabajo puede contener objetos de base de datos abiertos se crean en su propia colección de bases de datos.  En MFC, un área de trabajo es principalmente administrador de transacciones, especificando un conjunto de bases de datos abierto todo el mismo “espacio de la transacción.”  
  
> [!NOTE]
>  Las clases de base de datos de DAO son distintas de las clases de base de datos MFC basadas en ODBC.  Todos los nombres de clase de base de datos DAO ofrecen un prefijo “CDao”.  las clases MFC basadas en DAO son generalmente más capaces que las clases MFC basadas en ODBC.  Las clases DAO tienen acceso a datos a través del motor de base de datos Microsoft Jet, incluidos los controladores ODBC.  También admiten operaciones \(DDL\) de lenguaje de definición de datos, como crear bases de datos y agregar las tablas y los campos a través de las clases, sin tener que llamar a DAO directamente.  
  
## Funciones  
 La clase `CDaoWorkspace` proporciona lo siguiente:  
  
-   Acceso explícito, si es necesario, a un área de trabajo predeterminada, creada inicializar el motor de base de datos.  Normalmente se utiliza el área de trabajo predeterminada de DAO implícitamente haciendo la base de datos y objetos de conjunto de registros.  
  
-   Un espacio de la transacción en la que las transacciones se aplican a todas las bases de datos abierto en el área de trabajo.  Puede crear áreas de trabajo adicionales para administrar espacios separados de la transacción.  
  
-   Una interfaz a muchas propiedades del motor de base de datos Microsoft Jet subyacente \(vea las funciones miembro static\).  Abriendo o creando un área de trabajo, o llamar a una función miembro estática antes de abierto o cree, inicialice el motor de base de datos.  
  
-   Acceso a la colección de áreas de trabajo del motor de base de datos, que almacena todas las áreas de trabajo activos que se han anexada a.  También puede crear y ejecutar las áreas de trabajo sin anexarlas a la colección.  
  
## Seguridad  
 MFC no implementa las colecciones de los usuarios y grupos en DAO, que se utilizan para el control de seguridad.  Si necesita los aspectos de DAO, debe programarlas usted mismo a través de llamadas directas a las interfaces de DAO.  Para obtener información, vea [nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## Uso  
 Puede utilizar la clase `CDaoWorkspace` :  
  
-   Explícitamente abra el área de trabajo predeterminada.  
  
     El uso del área de trabajo predeterminada suele implícitamente — cuando se abren los nuevos objetos de [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) o de [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .  Pero puede que necesite tener acceso explícitamente \(por ejemplo, las propiedades del motor de base de datos de acceso o colección de áreas de trabajo.  Vea “uso Implicit del área de trabajo predeterminada”.  
  
-   Crear nuevas áreas de trabajo.  Llame a [Anexar](../Topic/CDaoWorkspace::Append.md) si desea agregarlos a la colección de áreas de trabajo.  
  
-   Abra un área de trabajo existente en la colección de áreas de trabajo.  
  
 Crear una nueva área de trabajo que no existe en la colección de áreas de trabajo se describe en función de miembro de [Crear](../Topic/CDaoWorkspace::Create.md) .  Los objetos del área de trabajo no se mantienen en ningún modo entre las sesiones del motor de datababase.  Si a uninitialize los vínculos de aplicación MFC estáticamente, finalizando la aplicación el motor de base de datos.  Si se a uninitialize los vínculos de aplicación con MFC dinámicamente, el motor de base de datos cuando se descarga el archivo DLL de MFC.  
  
 Explícitamente abriendo el área de trabajo predeterminada, o un área de trabajo existente en las áreas de trabajo colección, se describe en función de miembro de [Abrir](../Topic/CDaoWorkspace::Open.md) .  
  
 Finalizar una sesión del área de trabajo cerrando el área de trabajo con la función miembro de [Cerrar](../Topic/CDaoWorkspace::Close.md) .  **Cerrar** cierra cualquier base de datos que no ha cerrado previamente, gira revertir las transacciones sin confirmar.  
  
## Transacciones  
 DAO administra transacciones en el nivel de área de trabajo; por consiguiente, las transacciones en un área de trabajo con bases de datos abierto de varias se aplican a todas las bases de datos.  Por ejemplo, si dos bases de datos tienen actualizaciones sin confirmar y llama a [CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md), todas las actualizaciones se confirman.  Si desea restringir transacciones en una única base de datos, necesita un objeto independiente del área de trabajo para él.  
  
## Uso implícito del área de trabajo predeterminada  
 MFC utiliza el área de trabajo predeterminada de DAO implícitamente en las circunstancias siguientes:  
  
-   Si crea un nuevo objeto de `CDaoDatabase` pero no lo hace a través de un objeto existente de `CDaoWorkspace` , MFC crea un objeto temporal del área de trabajo para usted, que corresponde DAO a predeterminado el área de trabajo.  Si lo hace para varias bases de datos, todos los objetos de base de datos se asociado al área de trabajo predeterminada.  Puede tener acceso al área de trabajo de una base de datos a través de un miembro de datos de `CDaoDatabase` .  
  
-   De igual forma, si crea un objeto de `CDaoRecordset` sin proporcionar un puntero a un objeto de `CDaoDatabase` , MFC crea un objeto de base de datos temporal y, por extensión, un objeto temporal del área de trabajo.  Puede tener acceso a la base de datos de un conjunto de registros, e indirectamente al área de trabajo, a través de un miembro de datos de `CDaoRecordset` .  
  
## otras operaciones  
 otras operaciones de base de datos también se proporcionan, por ejemplo la reparación de una base de datos dañada o compactar una base de datos.  
  
 Para obtener información sobre la denominación DAO directamente y sobre seguridad DAO, vea [nota técnica 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## Requisitos  
 **encabezado:** afxdao.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)