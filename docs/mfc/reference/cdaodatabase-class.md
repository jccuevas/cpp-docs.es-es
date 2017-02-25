---
title: "CDaoDatabase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoDatabase class"
  - "CDaoDatabase class, and workspace"
  - "CDaoDatabase class, vs. CDatabase class"
  - "CDatabase (clase), vs. CDaoDatabase class"
  - "clases de base de datos [C++], DAO"
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDaoDatabase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una conexión a una base de datos a través de la cual puede funcionar en los datos.  
  
## Sintaxis  
  
```  
class CDaoDatabase : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoDatabase::CDaoDatabase](../Topic/CDaoDatabase::CDaoDatabase.md)|Crea un objeto `CDaoDatabase`.  Llame a **Abrir** para conectar el objeto a una base de datos.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoDatabase::CanTransact](../Topic/CDaoDatabase::CanTransact.md)|Devuelve cero si las transacciones de las compatibilidad con bases de datos.|  
|[CDaoDatabase::CanUpdate](../Topic/CDaoDatabase::CanUpdate.md)|Devuelve cero si el objeto de `CDaoDatabase` es actualizable \(no de sólo lectura\).|  
|[CDaoDatabase::Close](../Topic/CDaoDatabase::Close.md)|Cierre la conexión.|  
|[CDaoDatabase::Create](../Topic/CDaoDatabase::Create.md)|Crea el objeto de base de datos subyacente de DAO e inicializa el objeto de `CDaoDatabase` .|  
|[CDaoDatabase::CreateRelation](../Topic/CDaoDatabase::CreateRelation.md)|define una nueva relación entre las tablas en la base de datos.|  
|[CDaoDatabase::DeleteQueryDef](../Topic/CDaoDatabase::DeleteQueryDef.md)|Elimina un objeto de tabla guardado en la colección de QueryDefs de base de datos.|  
|[CDaoDatabase::DeleteRelation](../Topic/CDaoDatabase::DeleteRelation.md)|elimina una relación existente entre las tablas en la base de datos.|  
|[CDaoDatabase::DeleteTableDef](../Topic/CDaoDatabase::DeleteTableDef.md)|elimina la definición de una tabla en la base de datos.  esto elimina la tabla real y todos sus datos.|  
|[CDaoDatabase::Execute](../Topic/CDaoDatabase::Execute.md)|ejecuta una consulta de acciones.  La llamada **Ejecutar** para una consulta que devuelve resultados produce una excepción.|  
|[CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md)|Devuelve la cadena de conexión utilizada para conectar el objeto de `CDaoDatabase` en una base de datos.  Se utiliza para ODBC.|  
|[CDaoDatabase::GetName](../Topic/CDaoDatabase::GetName.md)|devuelve el nombre de la base de datos actualmente en uso.|  
|[CDaoDatabase::GetQueryDefCount](../Topic/CDaoDatabase::GetQueryDefCount.md)|devuelve el número de consultas definido para la base de datos.|  
|[CDaoDatabase::GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md)|Devuelve información sobre una consulta especificada definido en la base de datos.|  
|[CDaoDatabase::GetQueryTimeout](../Topic/CDaoDatabase::GetQueryTimeout.md)|Devuelve el número de segundos después del cual se ha de tiempo de espera se de operaciones de consulta de base de datos.  Afecta a abierto todo posterior, agrega nuevo, actualización, y las operaciones de edición y otras operaciones en orígenes de datos ODBC \(solo\) como las llamadas de **Ejecutar** .|  
|[CDaoDatabase::GetRecordsAffected](../Topic/CDaoDatabase::GetRecordsAffected.md)|Devuelve el número de registros afectados por la última actualización, edición, o agregar la operación o mediante una llamada a **Ejecutar**.|  
|[CDaoDatabase::GetRelationCount](../Topic/CDaoDatabase::GetRelationCount.md)|Devuelve el número de relaciones definidas entre las tablas en la base de datos.|  
|[CDaoDatabase::GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md)|Devuelve información sobre una relación especificada definidas entre las tablas en la base de datos.|  
|[CDaoDatabase::GetTableDefCount](../Topic/CDaoDatabase::GetTableDefCount.md)|devuelve el número de tablas definido en la base de datos.|  
|[CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md)|Devuelve información sobre una tabla especificada en la base de datos.|  
|[CDaoDatabase::GetVersion](../Topic/CDaoDatabase::GetVersion.md)|Devuelve la versión del motor de base de datos asociada con la base de datos.|  
|[CDaoDatabase::IsOpen](../Topic/CDaoDatabase::IsOpen.md)|Devuelve cero si el objeto de `CDaoDatabase` está conectado actualmente a una base de datos.|  
|[CDaoDatabase::Open](../Topic/CDaoDatabase::Open.md)|establece una conexión a una base de datos.|  
|[CDaoDatabase::SetQueryTimeout](../Topic/CDaoDatabase::SetQueryTimeout.md)|Establece el número de segundos después del cual las operaciones de consulta de base de datos \(en orígenes de datos ODBC solo\) tiempo de espera.  Afecta a abierto todo posterior, agrega nuevo, la actualización, y operaciones de eliminación.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoDatabase::m\_pDAODatabase](../Topic/CDaoDatabase::m_pDAODatabase.md)|Un puntero al objeto de base de datos subyacente de DAO.|  
|[CDaoDatabase::m\_pWorkspace](../Topic/CDaoDatabase::m_pWorkspace.md)|Un puntero al objeto de [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) que contiene la base de datos y defina su espacio de la transacción.|  
  
## Comentarios  
 Para obtener información sobre los formatos de base de datos compatibles, vea la función miembro de [GetName](../Topic/CDaoWorkspace::GetName.md) trabajar.  Puede tener activo de uno o más objetos de `CDaoDatabase` al mismo tiempo en una “área de trabajo especificada,” representado por un objeto de [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) .  El área de trabajo mantiene una colección de objetos de base de datos abierto, denominada la colección de bases de datos.  
  
> [!NOTE]
>  Las clases de base de datos DAO de MFC son distintas de las clases de base de datos MFC basadas en ODBC.  Todos los nombres de clase de base de datos de DAO tienen el prefijo “CDao”.  fuentes de `CDaoDatabase` de la clase una interfaz similar a la de la clase [CDatabase](../../mfc/reference/cdatabase-class.md)de ODBC.  La diferencia principal es que `CDatabase` tiene acceso al DBMS con ODBC y un controlador ODBC para ese DBMS.  `CDaoDatabase` tiene acceso a datos a través de un Objeto de acceso a datos \(DAO\) basado en el motor de base de datos Microsoft Jet.  las clases MFC basadas en DAO son generalmente más capaces que las clases MFC basadas en ODBC; las clases DAO pueden tener acceso a los datos, incluidos mediante controladores ODBC, a través de su propio motor de base de datos.  Las operaciones admiten DAO de lenguaje de definición de datos de \(DDL\) las clases también, como tablas de suma mediante las clases, sin tener que llamar a DAO directamente.  
  
## Uso  
 Puede crear objetos de base de datos implícita, al crear objetos de conjunto de registros.  Pero también puede crear objetos de base de datos explícitamente.  Para utilizar una base de datos existente explícitamente con `CDaoDatabase`, realice una de las siguientes:  
  
-   Crea un objeto de `CDaoDatabase` , pasar un puntero a un objeto abierto de [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) .  
  
-   O cree un objeto de `CDaoDatabase` sin especificar el área de trabajo \(MFC crea un objeto temporal del área de trabajo\).  
  
 Para crear una nueva base de datos de Microsoft Jet \(.MDB\), crear un objeto de `CDaoDatabase` y llamar a su función miembro de [Crear](../Topic/CDaoDatabase::Create.md) .  No llame a **Abrir** después de **Crear**.  
  
 Para abrir una base de datos existente, crear un objeto de `CDaoDatabase` y llamar a su función miembro de [Abrir](../Topic/CDaoDatabase::Open.md) .  
  
 Cualquiera de estas técnicas anexa el objeto de base de datos de DAO a las bases de datos de colección del área de trabajo y abra una conexión a los datos.  Cuando se construye los objetos de [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), de [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), o de [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) para trabajar en la base de datos conectada, pase a los constructores para estos objetos un puntero al objeto de `CDaoDatabase` .  Cuando termine de usar la conexión, llame a la función miembro de [Cerrar](../Topic/CDaoDatabase::Close.md) y destruya el objeto de `CDaoDatabase` .  **Cerrar** cierra cualquier conjunto de registros que no ha cerrado previamente.  
  
## Transacciones  
 El procesamiento transaccional de transacción de base de datos se proporciona en el nivel de área de trabajo \(vea [BeginTrans](../Topic/CDaoWorkspace::BeginTrans.md), [CommitTrans](../Topic/CDaoWorkspace::CommitTrans.md), y las funciones miembro de [recuperación](../Topic/CDaoWorkspace::Rollback.md) de la clase `CDaoWorkspace`.  
  
## conexiones ODBC  
 La manera recomendada de trabajar con orígenes de datos ODBC es asociar tablas externas a una base de datos de Microsoft Jet \(.MDB\).  
  
## Colecciones  
 Cada base de datos mantiene sus colecciones de, definición de tabla, de conjunto de registros, y los objetos de la relación.  El miembro de `CDaoDatabase` de la clase funciona para manipular estos objetos.  
  
> [!NOTE]
>  Los objetos se almacenan en DAO, no en el objeto de base de datos MFC.  MFC proporciona clases para la definición, la tabla, y los objetos de conjunto de registros pero no para los objetos de la relación.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoDatabase`  
  
## Requisitos  
 **encabezado:** afxdao.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)